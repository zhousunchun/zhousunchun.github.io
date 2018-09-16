---
layout: post
title: Google Ceres学习
date: 2018-09-16
tags: SLAM | Tools
categories: slam
---



### 构建代价函数

### 通过代价函数构建待求解的优化问题

### 配置求解器参数并且求解问题

## Example　$$\min ||\frac{1}{2} (10-x)^2||$$

### 步骤１，构建代价函数

```c++
struct CostFunctor{
    template<typename T>
    bool operator()(const T* const x, T* residual) const 
    {
        residual[0] = T(10.0) - x[0];
        return true;
    }
};
```

### 步骤２，构建寻优问题

```c++
Problem problem;
CostFunction * cost_function = 
    new AutoDiffCostFunction<CostFunctor,1,1> (new CostFunctor); // 自动求导
problem.AddResidualBlock(cost_function,nullptr,&x); // 想问题中添加误差项
```



### 步骤３，配置并且运行求解器

```c++
Solver::Option options;
options.linear_solver_type = ceres::DENSE_QR; // 配置增量的方程解法
options.minimizer_progress_to_stdout = true; // 输出到cout
Solver::Summary summary; //优化信息
Solve(options, &problem,&sumary); // 求解
```



#### 结果

```c++
// 输出优化的简要信息
std::cout << sumary.BrefReport() << std::endl;
// 最终结果
std::cout << x << std::endl;
```

