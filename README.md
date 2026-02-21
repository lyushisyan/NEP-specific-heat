
[English](#english-version) | [中文](#中文版)

## English Version

# NEP-specific-heat

Phonon DOS and specific heat analysis for silicon nanostructures (thin film / nanowire / quantum dot) using NEP, with bulk and Debye comparisons.

## Publication

This repository contains the computational notebooks used in the publication below.
If you use this code or results, please cite:

[1] S. Liu, G. Zhang, F. Yin, A. A. Barinov, V. I. Khvesyuk, and N. Yang, *Temperature dependence of specific heat capacity of nanostructures via neuroevolution machine-learned potential*, Journal of Applied Physics **138**, 104301 (2025). https://doi.org/10.1063/5.0284002


## Project Notebooks

- `Bulk_Cv.ipynb`: bulk DOS, Cv, Debye comparison, cumulative Cv
- `Create.ipynb`: build Si thin film, nanowire, and quantum dot structures
- `DOS_Film.ipynb`: phonon DOS for thin films (optional dispersion plot)
- `DOS_Wire.ipynb`: phonon DOS for nanowires (optional dispersion plot)
- `DOS_Dot.ipynb`: discrete vibrational frequencies for quantum dots
- `Heat_Cap.ipynb`: aggregate Cv(T) and exponent n(T) across systems

## Environment

Recommended: conda with Python 3.10+

Dependencies:
- `numpy`
- `scipy`
- `pandas`
- `matplotlib`
- `ase`
- `seekpath`
- `calorine`
- `jupyter`

Example:

```bash
conda create -n ph3-env python=3.11 -y
conda activate ph3-env
pip install numpy scipy pandas matplotlib ase seekpath calorine jupyter
```

## Required File and Folders

- NEP model: `NEP/Si_2022_NEP3_3body.txt`
- Recommended folders:
  - `Structure/`
  - `DOS/`
  - `Cv/`
  - `n/`
  - `Fig/`

## Recommended Run Order

1. `Bulk_Cv.ipynb`
2. `Create.ipynb`
3. `DOS_Film.ipynb`
4. `DOS_Wire.ipynb`
5. `DOS_Dot.ipynb`
6. `Heat_Cap.ipynb`

`Heat_Cap.ipynb` depends on outputs from previous notebooks (`DOS/*`, `Cv/Cv_bulk.txt`, `n/n_bulk.txt`).

## Notebook I/O

### 1) `Bulk_Cv.ipynb`
Input: internally built bulk Si

Output:
- `DOS/DOS_Bulk_nep.txt`
- `Cv/Cv_bulk.txt`
- `n/n_bulk.txt`
- `Cv/cumulative_Cv_T*K.txt`
- `Fig/*`

### 2) `Create.ipynb`
Input: none

Output:
- `Structure/Si_film_*.xyz`, `Structure/Si_film_*.cif`
- `Structure/Si_wire_*.xyz`, `Structure/Si_wire_*.cif`
- `Structure/Si_dot_*.xyz`, `Structure/Si_dot_*.cif`

### 3) `DOS_Film.ipynb`
Input: `Structure/Si_film_*.xyz`

Output:
- `DOS/DOS_Si_film_*.txt`
- `Fig/Disp/Disp_DOS_Si_film_*.png` (conditional)

### 4) `DOS_Wire.ipynb`
Input: `Structure/Si_wire_*.xyz`

Output:
- `DOS/DOS_Si_wire_*.txt`
- `Fig/Disp/Disp_DOS_Si_wire_*.png` (conditional)

### 5) `DOS_Dot.ipynb`
Input: `Structure/Si_dot_*.xyz`

Output:
- `DOS/Freq_Si_dot_*.txt`

### 6) `Heat_Cap.ipynb`
Input:
- `DOS/DOS_Si_film_*.txt`
- `DOS/DOS_Si_wire_*.txt`
- `DOS/Freq_Si_dot_*.txt`
- `Cv/Cv_bulk.txt`
- `n/n_bulk.txt`

Output:
- structure-wise `Cv/*`
- structure-wise `n/*`
- `Fig/Cv_n_relative_3x2.png`
- `Fig/Cv_cumulative_*.png`
- `Fig/DOS_vs_frequency_*.png`

## Notes

- Frequency units may differ across notebooks; keep unit convention consistent in post-processing.
- Large meshes (e.g. `160x160x160`) are computationally expensive.
- If figure folders are missing:

```bash
mkdir -p Fig/Disp DOS Cv n Structure
```

---

## 中文版

# NEP-specific-heat

使用 NEP 势函数计算硅纳米结构（薄膜/纳米线/量子点）的声子 DOS 与比热，并与 bulk 及 Debye 模型对比。

## 发表

本仓库为以下论文发表时使用的计算代码。
如果你使用了本仓库代码或结果，请引用：

[1] S. Liu, G. Zhang, F. Yin, A. A. Barinov, V. I. Khvesyuk, and N. Yang, *Temperature dependence of specific heat capacity of nanostructures via neuroevolution machine-learned potential*, Journal of Applied Physics **138**, 104301 (2025). https://doi.org/10.1063/5.0284002

## 项目 Notebook

- `Bulk_Cv.ipynb`：计算 bulk 的 DOS、Cv、Debye 对比和累计 Cv
- `Create.ipynb`：生成 Si 薄膜、纳米线、量子点结构
- `DOS_Film.ipynb`：计算薄膜声子 DOS（可选色散图）
- `DOS_Wire.ipynb`：计算纳米线声子 DOS（可选色散图）
- `DOS_Dot.ipynb`：计算量子点离散振动频率
- `Heat_Cap.ipynb`：汇总不同结构的 `Cv(T)` 和 `n(T)`

## 环境依赖

建议使用 conda（Python 3.10+）。

依赖：
- `numpy`
- `scipy`
- `pandas`
- `matplotlib`
- `ase`
- `seekpath`
- `calorine`
- `jupyter`

示例：

```bash
conda create -n ph3-env python=3.11 -y
conda activate ph3-env
pip install numpy scipy pandas matplotlib ase seekpath calorine jupyter
```

## 必要文件与目录

- NEP 模型文件：`NEP/Si_2022_NEP3_3body.txt`
- 建议目录：
  - `Structure/`
  - `DOS/`
  - `Cv/`
  - `n/`
  - `Fig/`

## 推荐执行顺序

1. `Bulk_Cv.ipynb`
2. `Create.ipynb`
3. `DOS_Film.ipynb`
4. `DOS_Wire.ipynb`
5. `DOS_Dot.ipynb`
6. `Heat_Cap.ipynb`

`Heat_Cap.ipynb` 依赖前序输出（`DOS/*`、`Cv/Cv_bulk.txt`、`n/n_bulk.txt`）。

## 各 Notebook 输入/输出

### 1) `Bulk_Cv.ipynb`
输入：内部构建 bulk Si

输出：
- `DOS/DOS_Bulk_nep.txt`
- `Cv/Cv_bulk.txt`
- `n/n_bulk.txt`
- `Cv/cumulative_Cv_T*K.txt`
- `Fig/*`

### 2) `Create.ipynb`
输入：无

输出：
- `Structure/Si_film_*.xyz`、`Structure/Si_film_*.cif`
- `Structure/Si_wire_*.xyz`、`Structure/Si_wire_*.cif`
- `Structure/Si_dot_*.xyz`、`Structure/Si_dot_*.cif`

### 3) `DOS_Film.ipynb`
输入：`Structure/Si_film_*.xyz`

输出：
- `DOS/DOS_Si_film_*.txt`
- `Fig/Disp/Disp_DOS_Si_film_*.png`（条件触发）

### 4) `DOS_Wire.ipynb`
输入：`Structure/Si_wire_*.xyz`

输出：
- `DOS/DOS_Si_wire_*.txt`
- `Fig/Disp/Disp_DOS_Si_wire_*.png`（条件触发）

### 5) `DOS_Dot.ipynb`
输入：`Structure/Si_dot_*.xyz`

输出：
- `DOS/Freq_Si_dot_*.txt`

### 6) `Heat_Cap.ipynb`
输入：
- `DOS/DOS_Si_film_*.txt`
- `DOS/DOS_Si_wire_*.txt`
- `DOS/Freq_Si_dot_*.txt`
- `Cv/Cv_bulk.txt`
- `n/n_bulk.txt`

输出：
- 各结构 `Cv/*`
- 各结构 `n/*`
- `Fig/Cv_n_relative_3x2.png`
- `Fig/Cv_cumulative_*.png`
- `Fig/DOS_vs_frequency_*.png`

## 说明

- 不同 notebook 频率单位标注可能不完全一致，后处理时请统一单位口径。
- 大网格（如 `160x160x160`）计算开销较大。
- 若目录不存在可先创建：

```bash
mkdir -p Fig/Disp DOS Cv n Structure
```
