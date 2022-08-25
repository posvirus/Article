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

#A 13.7 TFLOPS/W Floating-point DNN Processor using Heterogeneous Computing Architecture with Exponent-Computing-in-Memory  
><font face="Times New Roman" >Lee J, Kim J, Jo W, et al. A 13.7 TFLOPS/W floating-point DNN processor using heterogeneous computing architecture with exponent-computing-in-memory[C]//2021 Symposium on VLSI Circuits. IEEE, 2021: 1-2.</font>

---

- **写作目的：**

  本文主要提出了一种使用指数计算内存（CIM）和尾数处理引擎的异构 bfloat16 计算架构。能够有效降低存储芯片的能耗并提高计算效率。

- **内容记录：**

  - 浮点数（FP）进行乘累加（MAC）运算时，指数与尾数涉及的运算。可见指数仅涉及加减，而尾数由于需实现相乘，需实现移位、加、减等运算：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823231032810.png" alt="image-20220823231032810" style="zoom:150%;" />

  - 传统的FP-CIM需要实现对指数与尾数的运算，因此耗费周期数较多，能耗较大，结构较为复杂。
  - 处理器的整体架构：

  ![image-20220823231130448](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823231130448.png)

  1. **异构计算架构**，包括**指数内存计算**（ECIM）与**尾数处理引擎**（MPE），能够有效降低能耗。
  2. 采用**无尾数指数计算**（MFEC），能够最小化指数与尾数间的通信代价，同时降低MAC能耗。
  3. 位线电荷复用，可降低总体访问能耗。

  - MFEC的具体原理，实现指数与尾数运算的相互隔离：

  ![image-20220823231520241](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823231520241.png)

  - 运算时序图，使用流水线以提高运算效率，减少运算耗费的周期数：

  ![image-20220823231542814](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823231542814.png)

- **批注：**

  - **bfloat16（BF16）**：一种深度学习中常用的浮点数格式，共16位其中有1位符号位，8位指数位与7位尾数位。
  - 低能耗、高精度、高效率一般是CIM技术的3种主要的改进方向，主要可以从CIM架构设计、算法设计、运算时序设计等方向进行优化。

---

#A 1.041-Mb/mm2 27.38-TOPS/W Signed-INT8 Dynamic-LogicBased ADC-less SRAM Compute-In-Memory Macro in 28nm with Reconfigurable Bitwise Operation for AI and Embedded Applications  
><font face="Times New Roman" >Yan B, Hsu J L, Yu P C, et al. A 1.041-Mb/mm 2 27.38-TOPS/W Signed-INT8 Dynamic-Logic-Based ADC-less SRAM Compute-in-Memory Macro in 28nm with Reconfigurable Bitwise Operation for AI and Embedded Applications[C]//2022 IEEE International Solid-State Circuits Conference (ISSCC). IEEE, 2022, 65: 188-190.</font>

---

- **写作目的：**

  本文主要介绍一种基于**动态逻辑**（Dynamic Logic）的无ADC的SRAM CIM宏，并与传统设计进行了性能对比。

- **内容记录：**

  - 无ADC SRAM CIM宏的总体架构：

    **外围电路**包括：字线驱动器与CIM输入控制（WLDCIC）、输入组合逻辑（ICL）、内存读写电路。

    **内部存储单元**由：6T SRAM单元+4T RPLU构成。

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/%E8%9C%82%E8%9C%9C%E6%B5%8F%E8%A7%88%E5%99%A8_fig.png" alt="蜂蜜浏览器_fig" style="zoom: 50%;" />

  - 动态逻辑计算电路（DCC）与本地可重构处理单元（RPLU）的机制：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823232331678.png" alt="image-20220823232331678" style="zoom:150%;" />

  - RPLU主要的工作机制是：通过输入逻辑电路（ICL）控制RPLU内部FET的开闭，从而实现不同的位运算（AND/XOR/OR）。
  - DCC的使用取代了ADC，减少了芯片占用面积；RPLU的使用使得运算可重构。
  - Post-sum电路设计，减少内存访问，提高空间利用效率：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823232433938.png" alt="image-20220823232433938" style="zoom:150%;" />

- **批注：**

  - 一般含有ADC的CIM架构，由于ADC的加入，外部电路会占据较大的空间，解决方法主要有以下几条：

    1. 使用基于**检测放大器**的处理方案。
    
    > <font face="Times New Roman" >Yan B, Li B, Qiao X, et al. Resistive Memory‐Based In‐Memory Computing: From Device and Large‐Scale Integration System Perspectives[J]. Advanced Intelligent Systems, 2019, 1(7): 1900068.</font>
    
    2. 使用全数字CIM设计。
    3. 使用本文中提及的动态逻辑计算电路（DCC）。
    
  - **VHP**：向量Hadamard积，即向量按元素相乘，其结果仍为向量。

---

#Unassisted True Analog Neural Network Training Chip  

> <font face="Times New Roman" >Kohda Y, Li Y, Hosokawa K, et al. Unassisted true analog neural network training chip[C]//2020 IEEE International Electron Devices Meeting (IEDM). IEEE, 2020: 36.2. 1-36.2. 4.</font>

---

- **写作目的：**

  本文主要介绍一种单纯借助模拟cross-point阵列实现MAC的神经网络训练芯片。

- **内容记录：**

  - 本文给出的cross-point阵列单元设计：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823233032859.png" alt="image-20220823233032859" style="zoom:150%;" />

  - 基于文献：

  > <font face="Times New Roman" >Kohda Y, Li Y, Hosokawa K, et al. Unassisted true analog neural network training chip[C]//2020 IEEE International Electron Devices Meeting (IEDM). IEEE, 2020: 36.2. 1-36.2. 4.</font>

  - 给出了这一阵列单元的简化结构：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823233246676.png" alt="image-20220823233246676" style="zoom:150%;" />

  ​		

  - 删去用于给反相器供电的线路，阵列单元可进一步简化为：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823233316868.png" alt="image-20220823233316868" style="zoom:150%;" />

  - 其中由YW输入差模信号使电流源输出恒定电流给电容$C$充电，电容$C$的电荷$Q$$/$电压$V_\text{cap}$表征了该单元的权重，且权重大小与输入脉冲的总脉宽呈正比。右侧的FET用于读出，而本文给出的cross-point阵列单元的右侧较为复杂，这主要是为实现训练NN时的前向传播过程与反向传播过程，前向传播时，$Xr$为输入，$Yr$为输出，$T5$、$T6$关闭，$T7$开启；反向传播时，$Yr$为输入，$Xr$为输出，$T5$、$T7$关闭，$T6$开启。
  - 本文中所使用的N×N cross-point阵列，其实就相当于一个N输入N输出的全连接层。
  - 用于训练NN的BP算法，这基于文献：

  > <font face="Times New Roman" >Gokmen T, Vlasov Y. Acceleration of deep neural network training with resistive cross-point devices: Design considerations[J]. Frontiers in neuroscience, 2016, 10: 333.</font>

  - 每一训练周期共分为3个过程：**正向传播过程**，**反向传播过程**，**权重更新过程**，这里主要考虑权重更新过程，由于一个N$\times$N cross-point阵列仅对应神经网络中的1个2层结构，于是权重更新可表示为：

  $$
  w_{ij}\leftarrow w_{ij}+\eta x_i\delta_j
  $$

  

  - 其中η为全局学习率，**可通过调整电流源的差模输入信号或调整后方的乘数进行改变**。同时，可对该权重更新方法进行简化：

  $$
  w_{ij}\leftarrow w_{ij}\pm\Delta w_\text{min}\sum\limits_{n=1}^{BL}A_i^n\wedge B_j^n
  $$

  - 使用随机比特流进行乘法运算，这基于文献：

  > <font face="Times New Roman" >Alaghi A, Hayes J P. Survey of stochastic computing[J]. ACM Transactions on Embedded computing systems (TECS), 2013, 12(2s): 1-19.</font>

  - 该文献中提出的一种仅使用AND门实现的随机乘法器（**近似运算**），2个随机比特流中含1的概率为$p_1$与$p_2$，则在通过AND门后的比特流含1的概率为$p_1p_2$，此即实现乘法：

  ![image-20220823234402565](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823234402565.png)![image-20220823234409106](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823234409106.png)

  - 测试用的模拟ASIC设计：

  ![image-20220823234430743](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220823234430743.png)

  - 读上图可知，使用3个模拟cross-point阵列，实现一个单隐层的NN，隐层包含100个神经元。最终使用标准MNIST数据集进行测试。准确率为92.7%。

- **批注：**

  - 一般用于训练NN的BP算法的实现：（这里对各变量采用神经网络中的常用记号）

    - **前向传播：**即使用一个样本对神经网络进行一次输入，计算各神经元的输出：

    $$
    \left\{\begin{matrix}
     z^{(l)}=w^{(l)}a^{(l-1)}+b\\
    a^{(l)}=\sigma(z^{(l)})
    \end{matrix}\right.
    $$

    

    - **后向传播：**计算该样本对应的输出层及隐层误差：

    $$
    \delta^{(L)}=\nabla _{a^{(L)}}C(\theta)\odot\sigma'(z^{(L)})\\
    \delta^{(l)}=((w^{(l+1)})^T\delta^{(l+1)})\odot\sigma'(z^{(l)})
    $$

    - **权重更新：**更新权重：

    $$
    \left\{\begin{matrix}
    w_{jk}^{(l)}:=w_{jk}^{(l)}-\alpha a_{k}^{(l-1)}\delta_j^{(l)}\\
    b_j^{(l)}:=b_j^{(l)}-\alpha\delta_j^{(l)}
    \end{matrix}\right.
    $$

  - 其中，前向传播与后向传播基本仅涉及VMM运算，易于使用cross-point阵列实现，而权重更新涉及到对单个阵列单元的处理，以及数乘运算。

  - **MNIST数据集**：美国国家标准与技术研究院收集整理的大型手写数字数据库，研究中常使用该数据集对NN进行训练，以NN识别手写数字的准确率作为NN性能的一个可视化指标。

- **文章创新点：**

  - 所有MAC均在模拟cross-point阵列上进行实现，无需数字系统的辅助。（但这种系统在权重更新时必须本身具有良好的对称性与线性，因此阵列单元的复杂度会上升）
  - 使用随机乘法器简化权重更新时的乘法运算。

---

# High-Density 3D Monolithically Integrated Multiple 1T1R MultiLevel-Cell for Neural Networks  

><font face="Times New Roman" >Esmanhotto E, Brunet L, Castellani N, et al. High-density 3D monolithically integrated multiple 1T1R multi-level-cell for neural networks[C]//2020 IEEE International Electron Devices Meeting (IEDM). IEEE, 2020: 36.5. 1-36.5. 4.</font>

---

- **写作目的：**

  本文主要介绍一种基于1T1R单元的3D RRAM阵列，能够实现阵列的高密度。同时基于该阵列研究了MLC（多位）编程后电导弛豫现象对器件存储位数与精度的影响。

- **内容记录：**

  - 对一些用于NN的RRAM的对比：

    1. 基于文献：
    
       > <font face="Times New Roman" >Robayo D A, Sassine G, Lopez J M, et al. Reliability and Variability of 1S1R OxRAM-OTS for High Density Crossbar Integration[C]//2019 IEEE International Electron Devices Meeting (IEDM). IEEE, 2019: 35.3. 1-35.3. 4.</font>
    
       文献中给出的1S1R1T单元，其中1S指Ovonic 阈值开关(OTS)，可以有效限制未选择单元存在的隐藏路径电流：
    
       ![image-20220824233020858](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824233020858.png)
    
       OTS的几种可能物理机制基于文献：
    
       > <font face="Times New Roman" >Zhu M, Ren K, Song Z. Ovonic threshold switching selectors for three-dimensional stackable phase-change memory[J]. MRS Bulletin, 2019, 44(9): 715-720.</font>
    
       主要有**thermal runaway模型**（热力学角度）、**field-induced nucleation模型**（晶体结构角度）、**electronic模型**（载流子角度）：
    
       ![image-20220824233147483](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824233147483.png)
    
    2. 基于文献：
    
       > <font face="Times New Roman" >Hsieh E R, Giordano M, Hodson B, et al. High-density multiple bits-per-cell 1T4R RRAM array with gradual SET/RESET and its effectiveness for deep learning[C]//2019 IEEE International Electron Devices Meeting (IEDM). IEEE, 2019: 35.6. 1-35.6. 4.</font>
    
       文献给出的1T4R单元设计，增加RRAM单元密度，但同时需要重新制定编程方案，同时相邻单元间由于共用1T会有干扰：
    
       ![image-20220824233348347](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824233348347.png)
    
    3. 本文中提出的1T1R单元3D RRAM架构：
    
       ![image-20220824233407022](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824233407022.png)
    
       相对平面RRAM位密度增加1.5倍。
    
  - 本文给出的2种电导映射方案：
  
    ![image-20220824233436411](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824233436411.png)
  
    1. 基于均值与方差的映射（**SBA**），每一电导水平由以下区间给出：
       $$
       \mu_i-\Delta\sigma_i<G<\mu_i+\Delta\sigma_i
       $$
       其中$\mu_i$为均值，$\Delta\sigma_i$为方差。
  
    2. 线性映射（LA）。
  
    在MLC编程时利用上图所示的迭代编程方案实现电导水平的调整。
  
  - 对MLC编程后电导弛豫现象的研究：
  
  ![image-20220824233950102](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824233950102.png)
  
  - 对2种电导映射方案（SBA/LA）的电导弛豫现象（t=60s后）的研究，较低水平的电导会发生较大偏移，无法使用：
  
  ![image-20220824234017394](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824234017394.png)
  
  - 验证电导弛豫现象并非由于设计问题导致，验证方法是对比不同设备的电导弛豫，显示该现象从设备到设备的均匀性。
  - 分别在MNIST数据集与ECG数据集上训练全连接NN，显示电导弛豫现象对NN应用的准确性影响不大。
  
- **批注：**

  - 有关电导水平与表示位数的关系：一般RRAM单元若能够表示$N$个电导水平，则代表其能够表示的位数为$\log_2N$，比如本文中的9位电导水平，其能实现3.17位的存储。
  - RRAM存储密度的提升主要基于2个方面：其一是对硬件架构的设计，使单位空间能容纳更多存储单元，其二是对单元多位存储能力的提升，使RRAM单元能够具有尽可能多的电导水平。
  - **BER（Bit Error Rate）**：用于衡量RRAM编程的准确性，数学上等于RRAM阵列编程错误的单元数与RRAM阵列的总单元数的比值，本文中认为BER<$10^{-3}$时符合要求。
  - 为什么电导弛豫现象对NN训练的准确率影响不大？因为**NN只对最终的分类精度有要求**，而对矩阵的精度没有过于严格的要求，因此可以对矩阵元素的权重进行一定程度的容错。而既然NN训练对电导弛豫现象有弹性，那么尽可能地增加RRAM单元的电导水平数便有利于增加NN最终的分类精度。

- **文章创新点：**

  - 设计了一种新型 3D（双层）RRAM架构，将 RRAM 的位密度相对于平面 RRAM 提高 1.5 倍。
  - 将 MLC 编程与 3D RRAM 设计综合应用，进一步提升 RRAM 的存储密度。
  - 将 RRAM 应用于对电导弛豫弹性较大的 NN 训练上。

---

#Fully Integrated Spiking Neural Network with Analog Neurons and RRAM Synapses  

><font face="Times New Roman" >Valentian A, Rummens F, Vianello E, et al. Fully integrated spiking neural network with analog neurons and RRAM synapses[C]//2019 IEEE International Electron Devices Meeting (IEDM). IEEE, 2019: 14.3. 1-14.3. 4.</font>

---

- **写作目的：**

  本文主要使用RRAM实现**脉冲神经网络（SNN）**的一次完整集成。实验实现的NN结构为感知机，并使用MNIST数据集进行训练，训练后实现了84%的分类准确率。

- **内容记录：**

  - 基于N2D2（Neural Network Design and Deployment）学习框架实现SNN：

    ![image-20220824234724627](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824234724627.png)

    首先，使用**BP算法**训练DNN，其次，将DNN中的相关变量（权重，输入，输出，阈值等）转换（等价映射）至SNN中。

  - 基于文献：

    > <font face="Times New Roman" >Pérez-Carrasco J A, Zhao B, Serrano C, et al. Mapping from frame-driven to frame-free event-driven vision systems by low-rate rate coding and coincidence processing--application to feedforward ConvNets[J]. IEEE transactions on pattern analysis and machine intelligence, 2013, 35(11): 2706-2719.</font>

    文献给出了将一般NN中的变量映射至SNN中的方法：

    ![image-20220824235040435](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824235040435.png)![image-20220824235046328](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824235046328.png)

  - SNN的突触的物理结构：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/%E8%9C%82%E8%9C%9C%E6%B5%8F%E8%A7%88%E5%99%A8_fig1.png" alt="蜂蜜浏览器_fig1" style="zoom: 33%;" />

  - 本文中使用单极RRAM（SLC）单元实现突触，为实现多个权重水平，使用8个单极RRAM单元共同实现1个突触：

  ![image-20220824235321403](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220824235321403.png)

- **批注：**

  - 一般NN的神经元模型被称为**帧驱动模型**（frame-driven），而SNN使用的是如下所示的**事件驱动模型**（event-driven）:

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/figx.png" alt="figx" style="zoom:50%;" />

  - 该模型主要可实现如下功能：

  ![蜂蜜浏览器_fig3](https://raw.githubusercontent.com/posvirus/Image_storage/main/%E8%9C%82%E8%9C%9C%E6%B5%8F%E8%A7%88%E5%99%A8_fig3.png)

- **文章创新点：**

  - 首次在RRAM上完整集成了脉冲神经网络。降低了编程所需的功耗。
  - 使用多个单极RRAM实现MLC编程以模拟突触，增加了RRAM的单元密度。

---

# ECRAM as Scalable Synaptic Cell for High-Speed, Low-Power Neuromorphic Computing

><font face="Times New Roman" >Tang J, Bishop D, Kim S, et al. ECRAM as scalable synaptic cell for high-speed, low-power neuromorphic computing[C]//2018 IEEE International Electron Devices Meeting (IEDM). IEEE, 2018: 13.1. 1-13.1. 4.</font>

---

- **写作目的：**

  本文主要介绍一种基于$\text{Li}^+$嵌入$\text{WO}_3$的ECRAM（电化学存储器），能够实现高速、低功耗的神经形态计算。

- **内容记录：**

  - ECRAM单元的三端器件结构：

    ![image-20220825093358194](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825093358194.png)

    当读取时，连接源极与漏极，读取该器件的静态电导值作为结点的权重；当编程时，连接漏极与栅极，在栅极电流输入的控制下使Li+嵌入WO3中，改变器件电导。器件的完整结构：

    ![image-20220825093507972](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825093507972.png)

    同样需要外接电流源对栅极电流进行控制，电流源由FET组成。

  - 分别研究器件单元权重状态数、权重更新时的对称性、器件随机性在使用MNIST数据集训练时对分类精度的影响：

  ![image-20220825093547819](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825093547819.png)![image-20220825093552208](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825093552208.png)![image-20220825093558877](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825093558877.png)

  - ECRAM在权重更新对称性上与其余器件的对比，可见**多端器件**的优势所在：

  ![image-20220825093623585](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825093623585.png)

- **批注：**

  - 三端器件与二端器件作为RAM单元的对比：
    1. **二端器件**：常见的有RRAM、FeRAM、PCM等，二端器件的优势在于结构简单，易于集成，存储密度也相应较大。但相对应的在物理上的随机性与不均匀性也较为明显，通常需要更为复杂的算法或外部电路进行调制。（因其本身其实可以说是基于缺陷设计的器件）
    2. **三端/多端器件**：常见的是FET构成的单元，三端/多端器件的优势在于可以使读入与编程两个操作**去耦**，同时也使整个阵列具有更好的耐用性与更低的能耗，FET所具有的栅极可实现对电流，进而实现对单元权重的精确调控。

- **文章创新点：**

  - 使用基于$\text{Li}^+$嵌入$\text{WO}_3$的ECRAM进行神经形态运算，实现了高精度，高速及低功耗的目标。
  - 文中所提出的ECRAM在权重更新方面具有卓越的线性与对称性。

---

#Metal-oxide based, CMOS-compatible ECRAM for Deep Learning Accelerator  
><font face="Times New Roman" >  Kim  S, Todorov T, Onen M, et al. Metal-oxide based, CMOS-compatible ECRAM for deep  learning accelerator[C]//2019 IEEE International Electron Devices Meeting  (IEDM). IEEE, 2019: 35.7. 1-35.7. 4.  </font>

---

- **写作目的：**

  本文主要介绍一种基于金属氧化物结构的电化学存储器（MO-ECRAM），在展示其高速、低功耗、对称开关特性等优异性能的同时，首次通过实验演示了并行阵列操作、随机更新方案和零偏移技术。

- **内容记录：**

  - MO-ECRAM对称的开关特性：

  ![image-20220825094045643](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825094045643.png)

  - 分别以不同脉宽的脉冲测定其开关特性：

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/%E8%9C%82%E8%9C%9C%E6%B5%8F%E8%A7%88%E5%99%A8_1.png" alt="蜂蜜浏览器_1" style="zoom: 50%;" />

    分别在10$\mu s$/1$\mu s$/100$ns$/10$ns$的条件下测定其开关特性，脉宽越窄，最终运算速度越快，但相对应的对称性与开关比均会降低（因为单位脉冲变化的$\Delta G$会变小），但MO-ECRAM在10$\mu s$-10$ns$的范围内均显示出可观的开关特性。

  - 单位脉冲对应的电导更新值随脉宽、电压脉冲幅度、电流脉冲幅度的变化：

  ![image-20220825094406166](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825094406166.png)

  - 使用阵列演示顺序编程与并行编程，展示各单元间具有良好的独立性：

  ![image-20220825094426529](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825094426529.png)

  - 使用随机更新方案和零偏移技术进行阵列演示，零偏移技术可参考文献：

    > <font face="Times New Roman" >Kim et al., arXiv:1907.10228, (2019).  </font>

- **批注：**

  - 以下是基于$\text{Li}^+$的ECRAM的开关特性：

    ![image-20220825094600546](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825094600546.png)

    与MO-ECRAM对比，基于$\text{Li}^+$的ECRAM在编程与读取的交界处电导有明显的跃迁现象，可能与$\text{Li}^+$本身是否运动有关，值得研究。

  - 各单元间的读写之所以具有良好的独立性，是因为该阵列可选用电压脉冲进行读写，而电压脉冲与$\Delta G$呈指数关系，因此单元间较小的潜行电流对$\Delta G$的干扰相较编程电流本身会非常小。

- **文章创新点：**

  - 提出了MO-ECRAM这一具有良好性能的存算一体阵列单元。
  - 分别测定了电压脉冲与电流脉冲对$\Delta G$的调控，利用电压脉冲幅度与$\Delta G$的指数关系减小单元间编程的干扰。
  - 使用随机更新方案和零偏移技术进行阵列演示。

---

# Capacitor-based Cross-point Array for Analog Neural Network with Record Symmetry and Linearity  

><font face="Times New Roman" >  Li Y, Kim S, Sun X, et al. Capacitor-based cross-point array for analog neural network with record symmetry and linearity[C]//2018 IEEE Symposium on VLSI Technology. IEEE, 2018: 25-26. </font>

---

- **写作目的：**

  本文主要介绍一种基于电容器的cross-point阵列，可以实现目前最优的线性度与对称性，同时还讨论了在该阵列上应用**低泄漏DRAM**（low-leakage DRAM）技术的可能性。

- **内容记录：**

  - 基于电容器的阵列单元设计：

    ![image-20220825095228252](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825095228252.png)

    电流源左方的反相器为1个数字反相器+2个模拟反相器，数字反相器，模拟反相器的作用主要是利用XW_P与XW_N对输入差模信号VGP与VGN进行调制，进而调制电流源的电流输入。

  - cross-point阵列的构造：

  ![image-20220825095304316](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825095304316.png)

  - 对阵列单元编程并行性的测试（也可以说是对各单元间独立性的测试）：

    ![image-20220825095330362](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825095330362.png)

    读图可知，2$\times$2阵列中，各单元的权重更新值$\Delta V$在并行编程时保持独立与线性。

  - 对电容保持时间的测试：

    ![image-20220825095413594](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825095413594.png)

    保持时间的量级为1s，因此如果权重更新所经历的时间量级小于保持时间，那么在权重更新过程中便无需进行单元刷新。

- **批注：**

  - 基于电容器设计的阵列单元的优点：相较于基于NVM设计的阵列单元，电容器单元在权重更新时具有更高的精度，同时使用电容器单元的阵列在NN训练中也不需要进行定时刷新，因为单元权重在训练期间本身会不断更新。这解决了电容器单元阵列存储信息具有易失性的缺陷。

- **文章创新点：**

  - 设计了一种基于电容器的cross-point阵列，在开关特性上可以实现目前最优的线性度与对称性。
  - 利用该阵列高速读写的特性，使电容器在NN训练中无需进行刷新，巧妙避开了利用电容器存储权重信息易失的缺陷。

---

#Experimental Demonstration of Non-volatile Capacitive Crossbar Array for In-memory Computing 

><font face="Times New Roman" >  Luo Y C, Hur J, Wang T H, et al. Experimental demonstration of non-volatile capacitive crossbar array for in-memory computing[C]//2021 IEEE International Electron Devices Meeting (IEDM). IEEE, 2021: 1-4.</font>

---

- **写作目的：**

  本文通过实验演示了基于铁电材料$\text{Hf}_{0.5}\text{Zr}_{0.5}\text{O}_2$的电容式cross-point阵列在内存运算方面的应用。

- **内容记录：**

  - $\text{TiN/HZO/TiN}$电容器cross-point阵列的制作过程：

    ![image-20220825095900810](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825095900810.png)

    使用**等离子体增强原子层沉积技术（plasma-enhanced atomic layer deposition, PEALD）**进行器件制作。

  - 电容式cross-point阵列与传统1T1R阵列的对比：

    ![image-20220825095947176](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825095947176.png)

    1. 1T1R式同时具备静态与动态功耗（因其阵列是导通的，会存在静态电流），电容式仅具有动态功耗。
    2. 1T1R式的开关比较小，而电容式的则较大。
    3. 1T1R式较难进行3D堆叠，而电容式进行3D堆叠的可能性较大。

  - 1/3 $V_\text{w}$写入方案下可能引发的误差：

    ![image-20220825100059698](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825100059698.png)

    造成误差的主要原因是，在这种编程方案下，除被选中的单元外，其余的一些单元也会存在较小的电势差，这可能会引发错误，但按本文中的实验，所引发的错误率均在方案所设置的裕度内。

- **批注：**

  - **BEOL**与**FEOL**：
    - **BEOL（back end of line）**是IC制造的第二部分，其中各个器件（晶体管，电容器，电阻器等）与晶圆上的布线（金属化层）互连。
    - **FEOL（front end of line）**是IC制造的第一部分，其中各个组件（晶体管，电容器，电阻器等）在半导体中图案化。

---

# Nanosecond protonic programmable resistors for analog deep learning  

><font face="Times New Roman" >Onen M, Emond N, Wang B, et al. Nanosecond protonic programmable resistors for analog deep learning[J]. Science, 2022, 377(6605): 539-543.</font>

---

- **写作目的：**

  本文主要介绍一种可用于实现模拟DNN的质子可编程电阻（protonic programmable resistor），在具有良好的对称性与线性的同时能达到纳秒级的编程速度。并基于此器件讨论基于固态离子的ECRAM用于模拟人工突触的速度极限。

- **内容记录：**

  - **为什么要选择固态离子器件模拟人工突触**：水溶液中的离子只能实现毫秒级的反应速度，这并非是离子本身的限制，而是由于为使离子的速度更快，必然需要更大的外部电压，而液态水在高电压下会分解，从而从根本上限制了离子的速度上限。
  - 提升器件编程速度的两大主要方向：**尽可能高的外部电压**和**尽可能小的器件尺寸**，高电压提升的是器件内粒子的驱动力，小器件尺寸缩小的是粒子的运动距离。
  - 本文设计的质子可编程电阻的结构及TEM图像：

  ![image-20220825100545730](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825100545730.png)

  ​		采用$\text{Pd}$作为栅控材料，$\text{WO}_3$作为导电通道，纳米多孔PSG（无机磷硅酸盐玻璃）作为质子SE。

  - 质子可编程电阻表现出的高速与低能耗的编程特性：

  ![image-20220825100700793](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825100700793.png)

  - 该器件的转移特性（栅控特性）：
    $$
    I_G(V_\text{pulse})\propto\sinh(\frac{qaV_\text{pulse}}{2k_BTd_\text{PSG}})
    $$
    由此得出的关系式：
    $$
    \Delta G=kt_\text{pulse}^\beta\sinh(\frac{qaV_\text{pulse}}{2k_BTd_\text{PSG}})
    $$

  - 在长脉宽脉冲作用下器件可能会退化，主要是由于$\text{PSG}-\text{WO}_3$界面会有太多高能质子聚集，并可能产生$\text{H}_2$：

  ![image-20220825101047794](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825101047794.png)

- **批注：**

  - 用于模拟DNN的器件对**权重保持耐久性**与**状态切换精确性**的权衡：应当优先考虑状态切换时的精确性，因为在DNN的训练中，权重实际上是在不断更新的，我们实际上只需保证权重能够保持至下一次权重更新时即可，而无需对其进行太长时间的保存。NN训练的目的并非为了记住训练集，而是为从训练集中获取分类的依据，分类的精确性取决于对权重调整的精确性，而非记忆的持久性。

  - 解释公式：
    $$
    \Delta G=kt_\text{pulse}^\beta\sinh(\frac{qaV_\text{pulse}}{2k_BTd_\text{PSG}})
    $$
    由于：
    $$
    I_G(V_\text{pulse})\propto\sinh(\frac{qaV_\text{pulse}}{2k_BTd_\text{PSG}})
    $$
    可知电导$G$为$I_G$对$V_\text{pulse}$的导数，应当正比与$\cosh(\frac{qaV_\text{pulse}}{2k_BTd_\text{PSG}})$，而$\Delta G$则为$G$对时间$t_\text{pulse}$的微分，因此会有上式。
---

# Memory-Logic Hybrid Gate with 3D-Stackable Complementary Latches for FinFET-based Neural Networks  

><font face="Times New Roman" >Lee C, Chih Y D, Chang J, et al. Memory-logic hybrid gate with 3D-stackable complementary latches for FinFET-based neural networks[C]//2019 IEEE International Electron Devices Meeting (IEDM). IEEE, 2019: 38.7. 1-38.7. 4.</font>

---

- **写作目的：**

  本文主要介绍一种基于FinFET调控与RRAM编程的**互补锁存器结构**（complementary latch, CL），研究了其稳定性与耐久性，并基于此对其用于3D堆叠的拓展性进行了讨论。

- **内容记录：**

  - 单层CL的电路原理与真值表：

    ![image-20220825102422635](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825102422635.png)

    当S=0，即FinFET关断时，CL处于读状态；当S=1，即FinFET开启时，CL处于写状态。

  - 单层CL的物理结构与TEM图像：

  ![image-20220825102452412](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825102452412.png)

  - 物理结构中，Via1与M1及其中部介质构成了$R_1$与$R_2$，M2相当于电路原理图中的$Y$。

  - 对器件间均匀性的测试：

    ![image-20220825102618317](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825102618317.png)

    虽然器件与器件间的HRS与LRS状态存在着较大的偏移，但是由于RRAM具有较大的开关比HRS/LRS，因此在CL中由于$R_1$与$R_2$的互补性，输出$Y$并不会有较大偏移：

    ![image-20220825102651173](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825102651173.png)

  - 3D堆叠的拓展：

    ![image-20220825102714880](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825102714880.png)![image-20220825102719874](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825102719874.png)

    其中M5为输出$Y$，Via3与M3构成$R_3$与$R_4$，Via1与M1分别构成$R_1$与$R_2$，$R_5$与$R_6$。

- **批注：**

  - 采用FinFET器件的优势：FinFET器件在抑制亚阈值电流和栅极漏电流方面有着绝对的优势。FinFET的双栅或半环栅等体鳍形结构增加了栅极对沟道的控制面积，使得栅控能力大大增强，从而可以有效抑制短沟效应，减小亚阈值漏电流。

  - 使用镜像结构抑制$R_1$与$R_2$的不对称性：

    ![image-20220825102841274](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825102841274.png)

    这类似于差分放大器的设计思路，当某一侧的$R_1$与$R_2$因制造而存在较大差异时，另一侧的$R_1$与$R_2$便会对其进行调制。

- **文章创新点：**

  - 使用FinFET器件与RRAM组成TR结构，具有更好的调控性。
  - 构造**镜像器件**减小因器件自身缺陷产生的误差。
  - 讨论了器件用于3D堆叠的可能性。

---

# 3D RRAMs with Gate-All-Around Stacked Nanosheet Transistors for In-Memory-Computing  

><font face="Times New Roman" >Barraud S, Ezzadeen M, Bosch D, et al. 3D RRAMs with gate-all-around stacked nanosheet transistors for in-memory-computing[C]//2020 IEEE International Electron Devices Meeting (IEDM). IEEE, 2020: 29.5. 1-29.5. 4.</font>

---

- **写作目的：**

  本文主要介绍一种可进行3D堆叠的1T1R RRAM，在介绍其基本结构的同时，利用TCAD仿真对晶体管参数进行优化，最后讨论**SCL（Scouting Logic）**在该结构设计上的可行性。

- **内容记录：**

  - 本文介绍的1T1R RRAM的结构：

    ![image-20220825103228625](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825103228625.png)

    通过字线（WL）控制1T的栅极，确定选中单元的$z$坐标；通过源极线（SL）控制1R，确定选中单元的$x$坐标；通过位线（BL）与SL结合控制对单元的读写，同时确定选中单元的$y$坐标。

  - 在制造RRAM时，通过将BL进行金属化，将BL的电阻率降低至原值的$10^{-3}$：

  ![image-20220825103319523](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825103319523.png)

  - 使用TCAD仿真对晶体管性能进行优化设计，具体包括：

    1. 对通道掺杂浓度的讨论：

       ![image-20220825103410093](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825103410093.png)

       不同掺杂浓度下的转移特性曲线。

       掺杂浓度越高，静电特性越好，但对应的$I_\text{ON}$更大，对应着更大的功耗。

    2. 对导电通道宽度的讨论：

       ![image-20220825103454286](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825103454286.png)![image-20220825103459456](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825103459456.png)

    导电沟道宽度越宽，对应着更大的功耗，但对较窄的导电沟道，又容易引发**DIBL效应**。

  - 1T1R RRAM实现SCL的原理：

  ![image-20220825103550795](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825103550795.png)

- **批注：**

  - **DIBL效应（Drain-induced Barrier Lowering）**：在导电沟道宽度较小时，可能会引发因源漏区过于靠近而引发沟道势垒的下降，从而导致漏电的增加，同时降低Vth：

  ![image-20220825103617638](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825103617638.png)

  - **SCL（Scouting Logic）**：中文直译为侦察逻辑，一种新型逻辑设计，通过对忆阻器阵列的读取，利用基尔霍夫定律与电流比较器实现任意逻辑门的功能，右图展示了AND门与OR门的实现方法。

- **文章创新点：**

  - 设计了可用于3D堆叠的1T1R RRAM结构。
  - 使用TCAD对晶体管参数进行优化，节约实际实验测试的成本。
  - 探究了基于1T1R RRAM实现SCL的可行性。同时在SCL中采用**DC（双编码）**，能取得相对**SC（单编码）**2倍的能效。

---

# Monolithic 3D Integration of High Endurance Multi-Bit Ferroelectric FET for Accelerating Compute-In-Memory  
><font face="Times New Roman" >Dutta S, Ye H, Chakraborty W, et al. Monolithic 3D integration of high endurance multi-bit ferroelectric FET for accelerating compute-in-memory[C]//2020 IEEE International Electron Devices Meeting (IEDM). IEEE, 2020: 36.4. 1-36.4. 4.</font>

---

- **写作目的：**

  本文主要介绍一种基于FeFET的3D-CIM架构设计，对其制造工艺进行了详细描述，同时对其制造工艺的条件对最终器件性能的影响做了讨论，最后讨论了该CIM架构在实际运算时的性能。

- **内容记录：**

  - 传统CIM架构与**Monolithic 3D（M3D）** CIM架构的对比：

    ![](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825104222143.png)

    传统的CIM架构将NVM器件单元与外围电路共同安排于FEOL中，而M3D CIM架构将NVM器件单元安排于BEOL中（3D），同时在能耗、面积方面相对传统CIM架构具有显著的优势。

  - 本文设计的1T1FeFET单元：

    ![image-20220825104353235](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825104353235.png)

    其中FeFET作为NVM单元实现存储功能，位于上层，通过BEOL工序实现，晶体管（1T）作为调控单元位于下层，通过FEOL工序实现。

  - 1FeFET1T器件的制造工序：

  ![image-20220825104426455](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825104426455.png)

  - 使用ALD沉积HfO2后，对退火条件进行改变，考虑不同退火条件下器件性能的变化：

  ![image-20220825104443716](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825104443716.png)

- **批注：**

  - 对FeFET来说，由于其采用铁电材料，其不像RRAM，开关特性由I-V曲线进行描述，而一般会由该铁电材料的**极化回线**（P-E loop）给出：

  ![image-20220825104503592](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825104503592.png)

- **文章创新点：**

  - 设计并实现了Monolithic 3D（M3D） CIM架构，具有高密度，低能耗的特点。
  - 对器件制作工艺中的条件进行讨论，探究了制作条件对器件性能的影响。

---

# Monolithic 3D Integration of Logic, Memory and Computing-In-Memory for One-Shot Learning  
><font face="Times New Roman" >  Li Y, Tang J, Gao B, et al.  Monolithic 3D Integration of Logic, Memory and Computing-In-Memory for  One-Shot Learning[C]//2021 IEEE International Electron Devices Meeting  (IEDM). IEEE, 2021: 21.5. 1-21.5. 4.  </font>

---

- **写作目的：**

  本文主要介绍一种可用于**一次学习（One-Shot Learning）**的M3D CIM架构，分别介绍了该架构的制造工艺以及最终的设备特性，最后，使用该架构实现了一次学习，实现了高准确率、高速与低能耗。

- **内容记录：**

  - 本文设计的M3D CIM架构的基本结构与制作工艺：

    ![image-20220825104811471](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825104811471.png)

    第一层为实现控制逻辑的CMOS电路，在FEOL中进行制造；第二层为基于$\text{HfAlO}_\text{x}$的1T1R阵列，在BEOL中进行制造；第三层为基于$\text{Ta}_2\text{O}_5$的2T2R阵列，在BEOL中进行制造。

  - 该M3D CIM架构中，第一层为基于$\text{Si}$的MOSFET，主要用于实现一些控制逻辑，同时作为数据输入的端口，第二层为RRAM，实现了具有2个卷积层与2个全连接层的CNN，第三层为**TCAM（Ternary Content Addressable Memory）**层，存储CNN中提取的特征并实现查找功能。

  - 探究制造第三层时是否会对第二层的器件特性产生影响：

  ![image-20220825105000953](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825105000953.png)

  ​		读图可知，在第三层制造前后，第二层的开关特性并未显著改变，表明了两层制造工艺的独立		性。

  - M3D CIM实现一次学习的示意图：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220825105036584.png" alt="image-20220825105036584" style="zoom:150%;" />

- **批注：**

  - 第三层所选取的2T为**碳纳米管FET（CNTFET）**，它以碳纳米管（CNT）作为导电沟道。
  - **对于制造第二层RRAM是否会对第一层CMOS电路有影响**：由于两者分属BEOL与FEOL，而本文中BEOL采用低温工艺，不会对FEOL中生成的层产生影响。

- **文章创新点：**

  - 设计并实现了一种可用于一次学习的M3D CIM架构，相对于传统GPU能够实现高准确率、高速与低能耗。
  - 在制造工艺上，三层的制造互不影响，相互独立，器件特性得以保存。

---

