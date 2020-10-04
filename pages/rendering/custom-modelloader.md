```
package net.trentv.gasesframework.client;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collection;
import java.util.HashMap;
import java.util.List;

import org.lwjgl.util.vector.Vector3f;

import com.google.common.base.Function;

import net.minecraft.client.renderer.block.model.BakedQuad;
import net.minecraft.client.renderer.block.model.BlockFaceUV;
import net.minecraft.client.renderer.block.model.BlockPartFace;
import net.minecraft.client.renderer.block.model.FaceBakery;
import net.minecraft.client.renderer.block.model.IBakedModel;
import net.minecraft.client.renderer.block.model.ItemCameraTransforms;
import net.minecraft.client.renderer.block.model.ItemOverrideList;
import net.minecraft.client.renderer.block.model.ModelRotation;
import net.minecraft.client.renderer.block.model.SimpleBakedModel;
import net.minecraft.client.renderer.texture.TextureAtlasSprite;
import net.minecraft.client.renderer.vertex.VertexFormat;
import net.minecraft.util.EnumFacing;
import net.minecraft.util.ResourceLocation;
import net.minecraftforge.client.model.IModel;
import net.minecraftforge.common.model.IModelState;
import net.trentv.gasesframework.GasesFramework;

public class ModelBlockGas implements IModel
{
	private FaceBakery bakery = new FaceBakery();
	private ResourceLocation texture = new ResourceLocation(GasesFramework.MODID, "block/gas_default");
	
	@Override
	public Collection<ResourceLocation> getDependencies()
	{
		return new ArrayList<ResourceLocation>();
	}

	@Override
	public Collection<ResourceLocation> getTextures()
	{
		ArrayList<ResourceLocation> a = new ArrayList<ResourceLocation>();
		a.add(texture);
		return a;
	}

	@Override
	public IBakedModel bake(IModelState state, VertexFormat format, Function<ResourceLocation, TextureAtlasSprite> bakedTextureGetter)
	{
		//facings in D-U-N-S-W-E order 
		List<BakedQuad> allQuads = Arrays.asList(
				getQuad(new Vector3f(0,0,0), new Vector3f(16,0 ,16), EnumFacing.DOWN, bakedTextureGetter), //DOWN
				getQuad(new Vector3f(0,0,0), new Vector3f(16,16,16), EnumFacing.UP, bakedTextureGetter), //UP
				getQuad(new Vector3f(0,0,0), new Vector3f(16,16,16), EnumFacing.NORTH, bakedTextureGetter), //NORTH
				getQuad(new Vector3f(0,0,0), new Vector3f(16,16,16), EnumFacing.SOUTH, bakedTextureGetter), //SOUTH
				getQuad(new Vector3f(0,0,0), new Vector3f(16,16,16), EnumFacing.WEST, bakedTextureGetter), //WEST
				getQuad(new Vector3f(0,0,0), new Vector3f(16,16,16), EnumFacing.EAST, bakedTextureGetter)  //EAST
				);
		HashMap<EnumFacing, List<BakedQuad>> faceQuads = new HashMap<EnumFacing, List<BakedQuad>>();
		for(int i = 0; i < EnumFacing.values().length; i++)
		{
			faceQuads.put(EnumFacing.VALUES[i], Arrays.asList(allQuads.get(i)));
		}
		SimpleBakedModel newModel = new SimpleBakedModel(allQuads, faceQuads, true, true, bakedTextureGetter.apply(texture), ItemCameraTransforms.DEFAULT, ItemOverrideList.NONE);
		return newModel;
	}

	private BakedQuad getQuad(Vector3f from, Vector3f to, EnumFacing direction, Function<ResourceLocation, TextureAtlasSprite> bakedTextureGetter)
	{
		return bakery.makeBakedQuad(from, to, new BlockPartFace(null, 0, texture.toString(), new BlockFaceUV(new float[]{0,0,16,16}, 0)),
				bakedTextureGetter.apply(texture), direction, ModelRotation.X0_Y0, null, true, true);
	}
	
	@Override
	public IModelState getDefaultState()
	{
		return null;
	}
}




package net.trentv.gasesframework.client;

import java.util.Arrays;
import java.util.List;

import net.minecraft.client.resources.IResourceManager;
import net.minecraft.util.ResourceLocation;
import net.minecraftforge.client.model.ICustomModelLoader;
import net.minecraftforge.client.model.IModel;
import net.trentv.gasesframework.GasesFramework;

public class IGasesModelLoader implements ICustomModelLoader
{

	@Override
	public void onResourceManagerReload(IResourceManager resourceManager)
	{
		
	}

	@Override
	public boolean accepts(ResourceLocation modelLocation)
	{
		List<String> path = Arrays.asList("gas_smoke");
		if(modelLocation.getResourceDomain().equals(GasesFramework.MODID))
		{
			if(path.contains(modelLocation.getResourcePath()))
			{
				return true;
			}
		}
		return false;
	}

	@Override
	public IModel loadModel(ResourceLocation modelLocation) throws Exception
	{
		if(modelLocation.getResourceDomain().equals(GasesFramework.MODID))
		{
			if(modelLocation.getResourcePath().contains("gas_"))
			{
				return new ModelBlockGas();
			}
		}
		return null;
	}
}
```
In your registerRenderers clientproxy:
```
ModelLoaderRegistry.registerLoader(new IGasesModelLoader());
```