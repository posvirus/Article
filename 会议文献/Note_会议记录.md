#Design-Technology Co-Optimizations (DTCO) for General-Purpose Computing In-Memory Based on 55nm NOR Flash Technology  
><font face="Times New Roman" >Feng Y, Chen B, Liu J, et al. Design-Technology Co-Optimizations (DTCO) for General-Purpose Computing In-Memory Based on 55nm NOR Flash Technology[C]//2021 IEEE International Electron Devices Meeting (IEDM). IEEE, 2021: 12.1. 1-12.1. 4.</font>

***

- **写作目的：**

  本文主要讨论基于55nm的 NOR flash（一种通用的CIM架构）的内存计算，并基于DTCO提出改善NOR flash性能的一些方法并予以实验验证。

- **内容记录：**

  - 55nm NOR flash的架构设计（1个存储单元表示4位数据（16个状态，QLC））：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821164234324.png" style="zoom:150%;" />

  - 使用**热空穴注入（HHI）**实现对单个存储单元的擦除操作（因为HHI是对栅极与漏极施加偏压，这两者分别与字线与位线相连，1条字线与1条位线恰好对应一个存储单元）：

  ![image-20220821164513760](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821164513760.png)

  - 对55nm NOR flash全面的可靠性表征，包括：保留特性，读取干扰（read disturbs, RD），随机信号噪声，耐久性。
  - 将读写操作的工作区域由亚饱和区转至亚阈区后，存储器对应性能的比较（亚阈区工作功耗更低，但相对应的精确性降低，干扰增加）：

  ![image-20220821164553614](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821164553614.png)

- **批注：**

  - **DTCO（设计工艺协同优化）**：指在选择设计方案与工艺方案时，工艺和设计相互协同，彼此协作满足新节点器件的要求。
  - flash存储单元的几种数据存储密度：

  ![image-20220821164659896](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821164659896.png)

  - 一般的NOR flash使用**热电子注入（CHEI）**实现对单个存储单元的写入操作，使用量子隧穿实现对**同一字线上所有存储单元的擦除操作**；一般的NAND flash的写入原理与NOR flash相同，而擦除是基于CHEI实现的。
  - 似乎本文对DTCO仅仅是提及，并没有结合工作进行详细的说明。

---

#Implementation of Discrete Fourier Transform using RRAM Arrays with Quasi-Analog Mapping for HighFidelity Medical Image Reconstruction  

><font face="Times New Roman" >Zhao H, Liu Z, Tang J, et al. Implementation of Discrete Fourier Transform using RRAM Arrays with Quasi-Analog Mapping for High-Fidelity Medical Image Reconstruction[C]//2021 IEEE International Electron Devices Meeting (IEDM). IEEE, 2021: 12.4. 1-12.4. 4.</font>

---

- **写作目的：**

  本文主要讨论利用RRAM阵列实现**离散Fourier变换（DFT）**，提出了一种新型的电导映射方法——**准模拟映射（quasi-analog mapping, QAM）**并将其性能与常用的**量化映射（quantized mapping, QM）**进行对比。

- **内容记录：**

  - 使用RRAM阵列实现DFT的原理，每个存储单元需要的电导状态数会随DFT数据点的增加而迅速增加：

  ![image-20220821165036246](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821165036246.png)

  - **QAM**与**QM**的对比：QAM（准模拟映射）其实就是以实际需要的电导值作为电导状态，并以之为中心设定写入裕度，QM（量化映射）则是预先设定好电导状态与写入裕度，而将需要的电导值量化至预先设定的电导状态，从电导状态的精确度来看，QAM会优于QM。

  ![image-20220821165117432](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821165117432.png)

  - 用于实现DFT的1T1R RRAM阵列及其TEM图像：

  ![image-20220821165138060](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821165138060.png)

  - 2D-DFT的具体实现原理：

  ![image-20220821165159408](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821165159408.png)

- **批注：**

  - QM一般用于实现DNN，因为DNN只对最终的分类精度有要求，而对矩阵的精度没有过于严格的要求，因此可以对矩阵元素的权重进行合理的量化，而对DFT，其变换矩阵的精度很大程度上影响了变换结果的精度，因此需要使用QAM提升矩阵元素权重的精度。
  - 采用QAM进行映射消耗的能量一般高于QM，但由于在DFT算法中，对变换矩阵的映射是一次性的，因此这种能量消耗的增加相比对应性能的提高，一般是可接受的。
  - INTRODUCTION Para2 Line10中的Fig. 4可能有误，应为Fig. 3。

---

#An 8-Mb DC-Current-Free Binary-to-8b Precision ReRAM Nonvolatile Computing-in-Memory Macro using Time-SpaceReadout with 1286.4 - 21.6TOPS/W for Edge-AI Devices  
> <font face="Times New Roman" >Hung J M, Huang Y H, Huang S P, et al. An 8-Mb DC-Current-Free Binary-to-8b Precision ReRAM Nonvolatile Computing-in-Memory Macro using Time-Space-Readout with 1286.4-21.6 TOPS/W for Edge-AI Devices[C]//2022 IEEE International Solid-State Circuits Conference (ISSCC). IEEE, 2022, 65: 1-3.</font>

---

- **写作目的：**

  本文主要对提升nvCIM性能的3个方案进行了介绍，分别为DCFTS-IMC、IVTC与HLTMC。

- **内容记录：**

  - current mode nvCIM面对的挑战：因直流导致的高计算与读取能耗；输出精度；单位计算周期内较长的计算延迟：

  ![image-20220821165949703](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821165949703.png)

  - 使用DCFTS-IMC方案避免使用直流电流，降低能耗：

  ![image-20220821170020327](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821170020327.png)

  - 在DCFTS-IMC方案中：

    1个计算周期=**输入计算阶段**（BIC-P）+**移位加法阶段**（DSA-P）=**外围电路复位**（SP-0）+**位线预充电**（SP-1）+**字线输入**（SP-2）+**移位加法阶段**（DSA-P）

  - 使用IVTC方案增加信号裕度，提高输出精度：

  ![image-20220821170150080](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821170150080.png)

  - 使用HLTMC方案缩短计算延迟：

  ![image-20220821170210031](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821170210031.png)

- **批注：**

  - IVTC方案的本质，其实就是通过对电流积分获得累积电荷量，这通过对前文图中的电容$C_2$充电实现，并将累积电荷量线性转化为电压$U$，通过电压$U$与某一阈值对比确定pMACV的取值，而这与直接通过$DL$电压与阈值比较确定pMACV取值相比有更大裕度：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821170346633.png" alt="image-20220821170346633" style="zoom:150%;" />

  - 本文的结构比较独特，整篇论文其实是对5张图的描述，而图中蕴含的信息量较大，分别从nvCIM面对的挑战，3种具体的方案设计以及测试评估进行描述。

---

