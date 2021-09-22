| Minecraft |        Forge        | Gradle Default | Gradle Maximum | ForgeGradle  | Mappings Default  |   Mappings Latest    | MCP  | Java Minimum | Java Maximum |  Promotion  | Notes |
| --------- | ------------------- | -------------- | -------------- | ------------ | ----------------- | -------------------- | ---- | ------------ | ------------ | ----------- | ----- |
| 1.6.4   | 9.11.1.964          | 1.8    | 2.8    | 1.0-SNAPSHOT | N/A                      | N/A                             | 8.11            | 6  | 8  |             | Requires Java 7 to setupDecompWorkspace |
| 1.6.4   | 9.11.1.965          | N/A    | N/A    | N/A          | N/A                      | N/A                             | 8.11            | 6  | 8  |             | Use Scala 1.10.2, Patch Failures |
| 1.6.4   | 9.11.1.1345         | N/A    | N/A    | N/A          | N/A                      | N/A                             | 8.11            | 6  | 8  | RB,LB       | Use Scala 1.10.2, Patch Failures |
| 1.7.2   | 10.12.0.1047        | 1.10   | 1.12   | 1.1-SNAPSHOT | N/A                      | N/A                             | 9.03            | 6  | 8  |             | Requires Java 7 to setupDecompWorkspace<br/> (which will fail due to hunks 8 & 9 of `net/minecraft/world/gen/structure/StructureVillagePieces.java.patch` not applying),<br/> Last 1.7.2 version for FG1.1 |
| 1.7.2   | 10.12.2.1161-mc172  | 1.12   | 2.14.1 | 1.2-SNAPSHOT | N/A                      | N/A                             | 9.03            | 6  | 8  | RB,LB       | |
| 1.7.10  |                     | N/A    | N/A    |              | N/A                      | stable_8                        | 9.08            | 6  | 8  | Mappings    | |
| 1.7.10  |                     | N/A    | N/A    |              | N/A                      | stable_9                        | 9.08            | 6  | 8  | Mappings    | |
| 1.7.10  |                     | N/A    | N/A    |              | N/A                      | stable_10                       | 9.08            | 6  | 8  | Mappings    | |
| 1.7.10  |                     | N/A    | N/A    |              | N/A                      | stable_11                       | 9.08            | 6  | 8  | Mappings    | |
| 1.7.10  | 10.13.4.1614-1.7.10 | 2.0    | 4.4.1  | 1.2-SNAPSHOT | Unspecified              | stable_12                       | 9.08            | 6  | 8  | RB,LB       | |
| 1.8     |                     | N/A    | N/A    |              | N/A                      | stable_15                       | 9.10            | 6  | 8  | Mappings    | |
| 1.8     |                     | N/A    | N/A    |              | N/A                      | stable_16                       | 9.10            | 6  | 8  | Mappings    | |
| 1.8     |                     | N/A    | N/A    |              | N/A                      | stable_17                       | 9.10            | 6  | 8  | Mappings    | |
| 1.8     | 11.14.3.1502        | 2.0    | 4.4.1  | 1.2-SNAPSHOT | snapshot_20141130        | stable_18                       | 9.10            | 6  | 8  |             | Last 1.8 version for FG1.2 & Seperate FML |
| 1.8     |                     | N/A    | 2.7    | 2.0.0        |                          |                                 | 9.10            | 6  | 8  | ForgeGradle | |
| 1.8     |                     | N/A    | 2.7    | 2.0.1        |                          |                                 | 9.10            | 6  | 8  | ForgeGradle | |
| 1.8     |                     | N/A    | 2.8    | 2.0.2        |                          |                                 | 9.10            | 6  | 8  | ForgeGradle | |
| 1.8     | 11.14.4.1563        | 2.7    | 4.9    | 2.0-SNAPSHOT | snapshot_20141130        | stable_18                       | 9.10            | 6  | 8  | RB          | add `-x getFernFlower` to gradle command when running setupDecompWorkspace<br> needs fernflower-fixed.jar in `.gradle\caches\minecraft` |
| 1.8     | 11.14.4.1577        | 2.7    | 4.9    | 2.0-SNAPSHOT | snapshot_20141130        | stable_18                       | 9.10            | 6  | 8  | LB          | add `-x getFernFlower` to gradle command when running setupDecompWorkspace<br> needs fernflower-fixed.jar in `.gradle\caches\minecraft` |
| 1.8.8   | 11.15.0.1655        | 2.7    | 4.9    | 2.1-SNAPSHOT | snapshot_20151122        | stable_20                       | 9.18            | 6  | 8  | LB          | No 1.8.8 RB |
| 1.8.9   | 11.15.1.2318-1.8.9  | 2.7    | 4.9    | 2.1-SNAPSHOT | stable_20                | stable_22                       | 9.19            | 6  | 8  | RB,LB       | |
| 1.9     | 12.16.1.1887        | 2.7    | 4.9    | 2.1-SNAPSHOT | snapshot_20160312        | stable_24                       | 9.24            | 6  | 8  | RB          | |
| 1.9     | 12.16.1.1938-1.9.0  | 2.7    | 4.9    | 2.1-SNAPSHOT | snapshot_20160312        | stable_24                       | 9.24            | 6  | 8  | LB          | |
| 1.9.4   | 12.17.0.2317-1.9.4  | 2.7    | 4.9    | 2.2-SNAPSHOT | snapshot_20160518        | stable_26                       | 9.28            | 6  | 8  | RB,LB       | |
| 1.10    | 12.18.0.2000-1.10.0 | 2.7    | 4.9    | 2.2-SNAPSHOT | snapshot_20160518        | stable_26                       | 9.31            | 6  | 8  | LB          | No 1.10 RB |
| 1.10.2  | 12.18.3.2511        | 2.14   | 4.9    | 2.2-SNAPSHOT | snapshot_20161111        | stable_29                       | 9.31            | 6  | 8  | RB,LB       | |
| 1.11    |                     |        |        |              |                          | stable_31                       | 9.35            | 6  | 8  | Mappings    | |
| 1.11    | 13.19.1.2189        | 2.14   | 4.9    | 2.2-SNAPSHOT | snapshot_20161111        | stable_32                       | 9.35            | 6  | 8  | RB          | |
| 1.11    | 13.19.1.2199        | 2.14   | 4.9    | 2.2-SNAPSHOT | snapshot_20161220        | stable_32                       | 9.35            | 6  | 8  | LB          | |
| 1.11.2  | 13.20.1.2588        | 2.14   | 4.9    | 2.2-SNAPSHOT | snapshot_20161220        | stable_32                       | 9.37            | 6  | 8  | RB,LB       | |
| 1.12    | 14.21.1.2387        | 2.14   | 4.9    | 2.3-SNAPSHOT | snapshot_20170624        | stable_39                       | 9.40            | 8  | 8  | RB          | |
| 1.12    | 14.21.1.2443        | 2.14   | 4.9    | 2.3-SNAPSHOT | snapshot_20170624        | stable_39                       | 9.40            | 8  | 8  | LB          | |
| 1.12.1  | 14.22.1.2478        | 2.14   | 4.9    | 2.3-SNAPSHOT | snapshot_20170624        | stable_39                       | 9.41            | 8  | 8  | RB          | |
| 1.12.1  | 14.22.1.2485        | 2.14   | 4.9    | 2.3-SNAPSHOT | snapshot_20170624        | stable_39                       | 9.41            | 8  | 8  | LB          | |
| 1.12.2  | 14.23.5.2847        | 2.14   | 4.9    | 2.3-SNAPSHOT | snapshot_20171003        | stable_39                       | 9.42            | 8  | 8  | Last FG2    | |
| 1.12.2  | 14.23.5.2855        | 2.14   | 5.6.4  | 3.+/4.1.+    | snapshot_20171003        | stable_39                       | 20200226        | 8  | 8  | RB,LB       | |
| 1.13    |                     | 4.9    | 5.6.4  | 3.+          |                          | stable_43                       |                 | 8  | 8  |             | |
| 1.13.1  |                     | 4.9    | 5.6.4  | 3.+          |                          | stable_45                       |                 | 8  | 8  |             | |
| 1.13.2  | 25.0.219            | 4.9    | 5.6.4  | 3.+          | snapshot_20180921-1.13   | stable_47                       | 20190213        | 8  | 8  | LB          | |
| 1.14    |                     | 4.9    | 5.6.4  | 3.+          |                          | stable_49                       |                 | 8  | 8  |             | |
| 1.14.1  |                     | 4.9    | 5.6.4  | 3.+          |                          | stable_51                       |                 | 8  | 8  |             | |
| 1.14.2  | 26.0.63             | 4.9    | 5.6.4  | 3.+          | snapshot_20190621-1.14.2 | stable_53                       | 20190603        | 8  | 8  | LB          | |
| 1.14.3  | 27.0.60             | 4.9    | 5.6.4  | 3.+          | snapshot_20190719-1.14.3 | stable_56                       | 20190624        | 8  | 8  | LB          | |
| 1.14.4  | 28.2.0              | 4.9    | 5.6.4  | 3.+          | snapshot_20190719-1.14.3 | stable_58                       | 20190829        | 8  | 8  | RB          | |
| 1.14.4  | 28.2.23             | 4.9    | 5.6.4  | 3.+          | snapshot_20190719-1.14.3 | official_1.14.4<br>MCP: stable_58 | 20190829      | 8  | 8  | LB          | |
| 1.15    | 29.0.4              | 4.9    | 5.6.4  | 3.+          | snapshot_20190719-1.14.3 | official_1.15<br>MCP: stable_60 | 20191212        | 8  | 8  | LB          | |
| 1.15.1  | 30.0.51             | 4.9    | 5.6.4  | 3.+          | snapshot_20190719-1.14.3 | official_1.15.1<br>MCP: snapshot_20201118-1.15.1 | 20191217 | 8  | 8  | LB | |
| 1.15.2  | 31.2.0              | 4.10.3 | 5.6.4  | 3.+          | snapshot_20200514-1.15.1 | official_1.15.1<br>MCP: snapshot_20201118-1.15.1 | 20200515 | 8  | 8  | RB | |
| 1.15.2  | 31.2.55             | 4.10.3 | 5.6.4  | 3.+          | snapshot_20200514-1.15.1 | official_1.15.2<br>MCP: snapshot_20201118-1.15.1 | 20200515 | 8  | 8  | LB | |
| 1.16.1  | 32.0.108            | 4.10.3 | 5.6.4  | 3.+          | snapshot_20200514-1.16   | official_1.16.1<br>MCP: snapshot_20200820-1.16.1 | 20200625 | 8  | 8  | LB | Newer mappings available at [Dogforce Games](https://www.dogforce-games.com/maven/de/oceanlabs/mcp/mcp_snapshot/) |
| 1.16.2  | 33.0.61             | 4.10.3 | 5.6.4  | 3.+          | snapshot_20200514-1.16   | official_1.16.2<br>MCP: snapshot_20200916-1.16.2 | 20200812 | 8  | 8  | LB | Newer mappings available at [Dogforce Games](https://www.dogforce-games.com/maven/de/oceanlabs/mcp/mcp_snapshot/) |
| 1.16.3  | 34.1.0              | 4.10.3 | 5.6.4  | 3.+          | snapshot_20200514-1.16   | official_1.16.3<br>MCP: snapshot_20201028-1.16.3 | 20200911 | 8  | 8  | RB | |
| 1.16.3  | 34.1.42             | 4.10.3 | 5.6.4  | 3.+          | snapshot_20201028-1.16.3 | official_1.16.3<br>MCP: snapshot_20201028-1.16.3 | 20201025 | 8  | 8  | LB | |
| 1.16.4  | 35.1.4              | 4.10.3 | 5.6.4  | 3.+          | snapshot_20201028-1.16.3 | official_1.16.4<br>MCP: snapshot_20210309-1.16.4 | 20201102 | 8  | 8  | RB | |
| 1.16.4  | 35.1.37             | 4.10.3 | 5.6.4  | 3.+          | snapshot_20201028-1.16.3 | official_1.16.4<br>MCP: snapshot_20210309-1.16.4 | 20201102 | 8  | 8  | LB | |
| 1.16.5  | 36.0.46             | 4.10.3 | 5.6.4  | 3.+          | official_1.16.5          | official_1.16.5<br>MCP: 20210309-1.16.5<br>Parchment: 2021.08.29 | 20210115 | 8  | 8  | Last FG3 | |
| 1.16.5  | 36.1.16             | 6.8.1  | 6.9.1  | 4.1.+        | official_1.16.5          | official_1.16.5<br>MCP: 20210309-1.16.5<br>Parchment: 2021.08.29 | 20210115 | 8  | 8  |             | |
| 1.16.5  | 36.1.65             | 6.9    | 6.9.1  | 4.1.+        | official_1.16.5          | official_1.16.5<br>MCP: 20210309-1.16.5<br>Parchment: 2021.08.29 | 20210115 | 8  | 8  | Last FG4 | |
| 1.16.5  | 36.2.0              | 7.1.1  | 7.2    | 5.1.+        | official_1.16.5          | official_1.16.5<br>MCP: 20210309-1.16.5<br>Parchment: 2021.08.29 | 20210115 | 8  | 8  | RB | |
| 1.16.5  | 36.2.5              | 7.1.1  | 7.2    | 5.1.+        | official_1.16.5          | official_1.16.5<br>MCP: 20210309-1.16.5<br>Parchment: 2021.08.29 | 20210115 | 8  | 8  | LB | |
| 1.17.1  | 37.0.59             | 7.2    | 7.2    | 5.1.+        | official_1.17.1          | official_1.17.1<br>Parchment: 2021.09.05                         | 20210706 | 16 | 16 | | First release of 1.17.1 which supports Mixins natively |
| 1.17.1  | 37.0.70             | 7.2    | 7.2    | 5.1.+        | official_1.17.1          | official_1.17.1<br>Parchment: 2021.09.05                         | 20210706 | 16 | 16 | LB | |
