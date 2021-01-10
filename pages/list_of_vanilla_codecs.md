This is an incomplete list of known DataFixerUpper Codecs and functions to create Codecs added to Minecraft as of MCP version snapshot 20200723-1.16.1

| Object  | Codec | Notes |
| ------------- | ------------- | ------------- |
| Boolean  | com.mojang.serialization.Codec.BOOL  | DFU Default Codec |
| Byte  | com.mojang.serialization.Codec.BYTE  | DFU Default Codec |
| Short  | com.mojang.serialization.Codec.SHORT  | DFU Default Codec |
| Integer  | com.mojang.serialization.Codec.INT  | DFU Default Codec |
| Long  | com.mojang.serialization.Codec.LONG  | DFU Default Codec |
| Float  | com.mojang.serialization.Codec.FLOAT  | DFU Default Codec |
| Double  | com.mojang.serialization.Codec.DOUBLE  | DFU Default Codec |
| String  | com.mojang.serialization.Codec.STRING  | DFU Default Codec |
| ByteBuffer  | com.mojang.serialization.Codec.BYTE_BUFFER  | DFU Default Codec |
| IntStream  | com.mojang.serialization.Codec.INT_STREAM  | DFU Default Codec |
| LongStream  | com.mojang.serialization.Codec.LONG_STREAM  | DFU Default Codec |
| Dynamic<?>  | com.mojang.serialization.Codec.PASSTHROUGH  | DFU Default Codec |
| IntStream  | com.mojang.serialization.Codec.INT_STREAM  | DFU Default Codec |
| Unit  | com.mojang.serialization.Codec.EMPTY  | DFU Default Codec |
| Property  | net.minecraft.state.func_241492_e_()  |  |
| WeightedList<U>  | net.minecraft.util.WeightedList.func_234002_a_(Codec<U> p_234002_0_)  |  |
| WeightedList.Entry<E>  | net.minecraft.util.WeightedList.Entry.func_234008_a_(final Codec<E> p_234008_0_)  |  |
| PointOfInterest  | net.minecraft.village.PointOfInterest.func_234150_a_(Runnable p_234150_0_)  |  |
| PointOfInterestData  | net.minecraft.util.PointOfInterestData.func_234158_a_(Runnable p_234158_0_)  |  |
| BlockPos | net.minecraft.util.math.BlockPos.field_239578_a_ |  |
| Vector3i | net.minecraft.util.math.vector.Vector3i.field_239781_c_ |  |
| Registry<T> | net.minecraft.util.registry.Registry<T> | Vanilla Registries implement Codec interface so can be directly used as one. |
