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

