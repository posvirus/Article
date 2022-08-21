# Metal–Oxide RRAM  

><font face="Times New Roman" >Wong H S P, Lee H Y, Yu S, et al. Metal–oxide RRAM[J]. Proceedings of the IEEE, 2012, 100(6): 1951-1970.</font>
***

- **写作目的：**

  本文简介可用于制造RRAM的MIM结构，同时介绍以此为基础的简单二元金属氧化物RRAM的工作原理、器件特性、性能指标与发展趋势。

- **内容记录：**

  - **单极型变阻**与**双极型变阻**：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/fig1-0.png" alt="fig1-0" style="zoom:80%;" />

  - Set-Reset切换机理以及Forming机理：

  ![fig1-1](https://raw.githubusercontent.com/posvirus/Image_storage/main/fig1-1.png)

  - 单极型Reset—电流热激活—$\text{O}^{2-}$扩散；双极型Reset—反偏电场驱动— $\text{O}^{2-}$漂移。
  - 一些值得关注的氧化层材料：$\text{HfO}_\text{x}$(High K)，$\text{AlO}_\text{x}$(提升均匀性)，$\text{NiO}$(1D1R结构)， $\text{TiO}_\text{x}$，$\text{TaO}_\text{x}$(耐久性好)。
  - 1T1R结构中的MOSFET充当了良好的电流限制器。
  - 触点RRAM通过直接在MOSFET的源极/漏极触点上制造RRAM，最大限度地减少了晶体管和RRAM之间互连的寄生电容。
  - RRAM空间的非均匀性与改进：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/fig1-2.png" alt="fig1-2" style="zoom:80%;" />

  - RRAM用于**MLC**：

  ![fig1-3](https://raw.githubusercontent.com/posvirus/Image_storage/main/fig1-3.png)

  - RRAM提供了 flash 所不具备的低编程电压和 DRAM 所不具备的非易失性，并且具有可与 DRAM 相媲美的速度。

- **批注：**

  - 两种不同的RRAM阵列架构：

    - **1T1R阵列：**

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/fig1-4.jpg" alt="fig1-4" style="zoom:67%;" />

    驱动电流会限制尺寸的缩小。

    - **cross-point阵列：**

    <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/fig1-5.jpg" alt="fig1-5" style="zoom:67%;" />

  - 理想的RRAM：forming-free、低功耗、低复位电流、Set时良好的电流限制、时间-空间的均匀性、耐久性（编程次数多）、非易失性（voltage-time dilemma）。

---

#Effect of Moisture Stress on the Resistance of $\text{HfO}_2/\text{TaO}_\text{x}$-Based 8-Layer 3D Vertical Resistive Random Access Memory  
><font face="Times New Roman" >Gao R, Lei D, He Z, et al. Effect of Moisture Stress on the Resistance of HfO 2/TaO x-Based 8-Layer 3D Vertical Resistive Random Access Memory[J]. IEEE Electron Device Letters, 2019, 41(1): 38-41.</font>
---

- **实验目的：**

  探究水分应力对8层3D Non-filament(非CF导电) VRRAM器件性能的影响。

- **实验方法：**

  - **“Measure-Stress-Measure” Scheme**，相当于前后对照。

  - 使用FPGA控制的自动化测试方法：

    | 间歇应力时间 | 累积应力时间 | 间歇应力时间 | 累积应力时间 |
    | :----------: | :----------: | :----------: | :----------: |
    |      0       |      0       |      3h      |    4.67h     |
    |    0.17h     |    0.17h     |     13h      |    17.67h    |
    |     0.5h     |    0.67h     |     44h      |    61.67h    |
    |      1h      |    1.67h     |     100h     |   161.67h    |

  - 间歇性施加应力，应力条件：85°C/85% 相对湿度(RH)。

  - 设置两组平行重复实验。

- **实验内容：**

  - 对独立设备，测定其$I-V$关系，$R_\text{HRS}$，$R_\text{LRS}$，电阻窗口，$I_\text{Reset}$随水分应力施加的退化。
  - 施加24h烘烤探究$R_\text{HRS}$，$R_\text{LRS}$，电阻窗口，$I_\text{Reset}$退化的可恢复性。
  - 对VRRAM的不同层（8层）分别进行测定，探究水分应力影响的层依赖性。

- **实验结果：**

  - $R_\text{HRS}$与电阻窗口随施加应力的时间推移而减少，$I_\text{Reset}$随时间推移而增加，且上述退化几乎无法恢复：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821101959136.png" alt="image-20220821101959136" style="zoom:150%;" />![image-20220821102012337](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821102012337.png)

  - 水分应力退化基本不具有层依赖性：

  ![image-20220821102116199](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821102116199.png)

- **批注：**

  - 3D-RRAM结构（以cross-point阵列为例）：

  ![image-20220821102200478](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821102200478.png)

  - 8层3D VRRAM架构：

  ![image-20220821102233738](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821102233738.png)<img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821102243264.png" alt="image-20220821102243264" style="zoom:150%;" />

  - **resistance window/电阻窗口**：应该是指$R_\text{HRS}-R_\text{LHS}$，一般希望越大越好。
  - 水分应力会引入额外的缺陷：

  ![image-20220821102359624](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821102359624.png)

---

# Filament-Free Bulk Resistive Memory Enables Deterministic Analogue Switching  
><font face="Times New Roman" >Li Y, Fuller E J, Sugar J D, et al. Filament‐Free Bulk Resistive Memory Enables Deterministic Analogue Switching[J]. Advanced Materials, 2020, 32(45): 2003984.</font>
---

- **写作目的：**

  介绍用于模拟开关的无CF（Filament-Free）的RRAM，可有效消除传统CF-RRAM用于模拟开关时的不确定性。

- **内容记录：**

  - **CF-RRAM**与**Bulk-RRAM**的对比（此处讨论的CF-RRAM的复位电流是$\text{O}^{2-}$被热激活扩散形成，因此应该是**单极型RRAM**）：

  <img src="https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821102724785.png" alt="image-20220821102724785" style="zoom:80%;" />

  - Bulk-RRAM的温度受外部独立控制，保证模拟开关的高度线性。
  - Bulk-RRAM电流总体分布的均匀性：

  ![image-20220821102814639](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821102814639.png)

  - Bulk-RRAM的耐久性与温度的关系：

  ![image-20220821102842766](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821102842766.png)

  - Bulk-RRAM本质上是一种ECRAM，它与一般ECRAM相比的优势在于其在小尺寸微缩时能保持耐久性（此处用$\tau_{RC}$表征）几乎不变：

  ![image-20220821102922076](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821102922076.png)

- **批注：**

  - 传统的CF-RRAM在用作数字开关是效果应该是较好的，因为只涉及双态，而在用作模拟开关时，由于需要阻态进行“准连续”的变化，此时由Forming过程中随机生成的CF控制电阻的不确定性便会增强。
  - 本文中无CF的RRAM通过在绝缘层中引入固体电解质YSZ，并在外界均匀加热，将对器件电阻的控制由CF中的氧空位推广至整个绝缘体中的氧空位，因此这种RRAM又称Bulk-RRAM。

---

#Impact of Multilevel Retention Characteristics on RRAM based DNN Inference Engine  
><font face="Times New Roman" >Shim W, Meng J, Peng X, et al. Impact of multilevel retention characteristics on RRAM based DNN inference engine[C]//2021 IEEE International Reliability Physics Symposium (IRPS). IEEE, 2021: 1-4.</font>
---

- **实验目的：**

  探究温度对多级$\text{HfO}_2$-RRAM保留特性的影响，以及对DNN推理精度的影响。

- **实验内容：**

  - 使用单个RRAM单元表示4位权重（2$\times$2），分别探究4种阻态在不同温度下的电导漂移情况，并最终测试不同温度下推理精度随时间的变化情况。

- **实验结果：**

  - 4种阻态下，RRAM单元的电导均随时间推移而下降，其中2、3状态由于是“中间状态”，电导的漂移尤其明显：

  ![image-20220821103316279](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821103316279.png)![image-20220821103323408](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821103323408.png)

  - 建模得出电导期望$\mu$与方差$\sigma$随时间与温度的变化模型：

  $$
  \Delta \mu=\mu(t)-\mu_\text{init}=A_\text{avg}\times\log t\\
  \Delta \sigma=\sigma(t)-\sigma_\text{init}=B_\text{var}\times\log t
  $$

  - 推理精度随温度、时间、以及位数的变化规律，位数越少，温度越低，RRAM保留特性越好，推理精度越高：

  ![image-20220821103633109](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821103633109.png)![image-20220821103642603](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821103642603.png)

  - 在具有1-4个权重的DNN推理模拟中，推理精度在55$^\circ C$及以上会显著下降。

- **批注：**

  - 传统的冯诺依曼计算架构中，需要存储器与运算器间进行频繁的数据交换，运算速度会受功耗与内存带宽限制，因此提出了**CIM**的概念。
  - CIM也需要单个RRAM单元表示多位，但比传统的MLC对其保持特性的要求更加严格。
  - RRAM单元处于“中间状态”（intermediate states）时，不稳定性会加剧。
  - 提升推理精度的可能方法：外加补偿电压减弱电导漂移的影响；对RRAM进行定时刷新；在软件层面上开发新的算法等。

---

#Impact of the Atomic Layer-Deposited Ru Electrode Surface Morphology on Resistive Switching Properties of $\text{TaO}_\text{x}$‑Based Memory Structures  

><font face="Times New Roman" >Koroleva A A, Chernikova A G, Chouprik A A, et al. Impact of the atomic layer-deposited Ru electrode surface morphology on resistive switching properties of TaOx-based memory structures[J]. ACS Applied Materials & Interfaces, 2020, 12(49): 55331-55341.</font>
---

- **实验目的：**

  探究通过REALD生成的Ru电极的表面形态对$\text{TaO}_\text{x}$-RRAM的RS特性的影响。

- **实验方法：**

  - 为保证实验时$\text{Ru}$的表面覆盖率约为1，防止$\text{TaO}_\text{x}$与$\text{TiN}$相互反应的干扰，将实验的REALD周期数设为45以上。
  - 考虑$\text{TaO}_\text{x}$与$\text{TiN}$生成$\text{TiO}_2$层可能的影响（实验表明影响不大）。
  - 设置空白对照组，将经过不同周期ALD处理的$\text{TiN}$/$\text{Ru}$/$\text{TaO}_\text{x}$/$\text{Ta}$器件与$\text{TiN}$/$\text{TaO}_\text{x}$/$\text{Ta}$器件RS特性进行对比。

- **实验内容：**

  - 分别测定不同ALD周期数下（0/60/110/200/500）器件BE的表面粗糙度。
  - 分别测定不同ALD周期数下（0/110/500）器件首次DC $I-V$曲线以及通过对同一器件多个样本测定的Forming电压大小。
  - 分别**多次**测定不同ALD周期数下（0/60/110/200/500）器件RS特性以及$R_\text{HRS}$，$R_\text{LRS}$的分布。
  - 分别**多次**测定不同ALD周期数下（0/60/110/200/500）器件的开关电压，耐久性（开关周期数）。
  - 分别测定不同ALD周期数下（0/110/200/500）器件的保持特性。
  - 就ALD周期数为500的器件具体研究其开关特性并给出原理解释。
  - 探究不同ALD周期数（110/200/500）对器件Forming过程中CF品质的影响。

- **实验结果：**

  - **BE的表面粗糙度随ALD周期数增加而增加，形成较厚的$\text{Ru}$层。**
  - Forming电压的均值与方差均随ALD周期数增加而减小。
  - $R_\text{HRS}/R_\text{LRS}$随ALD周期数增加而增大（说明电阻窗口更大），且阻态稳定性更强（方差更小）[1]。
  - 开关周期数随ALD周期数的增加而增加，器件开关电压的绝对值随ALD周期数的增加而变小。
  - 器件的保持特性随ALD周期数的增加而改善，具体表现为$R_\text{HRS}$与$R_\text{LRS}$的稳定性增强[2]。

  - 随ALD周期数增加，CF数量变少，但强度与稳定性增加。

  ![image-20220821105102326](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821105102326.png)

- **实验结论：**

  通过REALD生长的$\text{Ru}$电极的粗糙度（厚度）与$\text{TiN}$/$\text{Ru}$/$\text{TaO}_\text{x}$/$\text{Ta}$器件的RS特性相关，粗糙的$\text{Ru}$电极能降低器件的Forming与开关电压，提高器件的电阻窗口、耐久性、均匀性与保持特性，有助于增强器件性能与可靠性。

- **批注：**

  - **SCLC**：空间电荷限制电流。
  - [1]：为什么ALD周期数由200$\rightarrow$500时，$R_\text{HRS}$的方差反而变大？
  - [2]： $R_\text{HRS}$会随时间推移而增大，使电阻窗口变大
  - **本实验中，对RS特性起主要影响的是BE的粗糙度，而导致BE粗糙度不同的是ALD工艺的周期数。**
  - 一次完整的Set-Reset过程中的$I-V$特性及解释：

  ![image-20220821105605727](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821105605727.png)![image-20220821105613397](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821105613397.png)

---

#Understanding memristive switching via in situ characterization and device modeling  

><font face="Times New Roman" >Sun W, Gao B, Chi M, et al. Understanding memristive switching via in situ characterization and device modeling[J]. Nature communications, 2019, 10(1): 1-13.</font>
---

- **写作目的：**

  介绍忆阻器件研究的热点与最新进展；提出通过原位表征与物理建模研究忆阻器件的SR特性；展望忆阻器件未来商业化的可能性。

- **内容记录：**

  - 忆阻器件开关机制分类与研究现状（阳离子/阴离子/双离子）：

  ![image-20220821110109375](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821110109375.png)

  - 忆阻器件的开关机制的另一种分类（CF/interface/bulk）：

  ![image-20220821110145689](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821110145689.png)

  - 各种原位技术与物理建模的时空分辨率：

  ![image-20220821110219950](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821110219950.png)

  - 使用不同的原位技术研究忆阻器件SR特性的4个过程（离子迁移->离子积累->CF形成->Set-Reset循环）：

  ![image-20220821110249224](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821110249224.png)

  - 不同种类的模型：物理模型/紧凑模型/SPICE 模型：

  ![image-20220821110314524](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821110314524.png)

  - 不同物理建模方法（FP/分子动力学/蒙特卡罗法/FE）：

  ![image-20220821110333262](https://raw.githubusercontent.com/posvirus/Image_storage/main/image-20220821110333262.png)

- **批注：**
  - **in situ characterization**，原位表征，应该是指一种现场实时观测/测量技术。
  - 忆阻器件在硬件设备方面的两个挑战：**参数的随机可变性**与**器件的耐久性**。
  - 参数的随机可变性与器件的耐久性不是MOSFET面临的挑战，因为MOSFET是多子器件。相比之下，忆阻器件中的SR是通过有限数量的离子迁移通过切换层或在电极/切换层界面实现的，因此控制参与的离子更具挑战性。

---
