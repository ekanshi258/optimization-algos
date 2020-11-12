# Nature-Inspired Optimization
Applications of Nature-inspired optimization algos in real life Engineering settings

### Disclaimer:
Since I'm a computer science major, I'm not an expert in the fields of engineering to which these problems are related.  
I'm only solving mathematical models of the problems using my knowledge of evolutionary algos, and have obtained these models from research papers in those fields. If there are any mistakes in the terminology I have used, or any issue with the maths behind the paper or translation of the math into my code, please let me know and I will be happy to correct them. Thanks!

> **Note**: Not able to view the `ipynb`s? Please follow [these instructions](https://github.com/iurisegtovich/PyTherm-applied-thermodynamics/issues/11#issue-184473171):  
>
> Open the `ipynb` using `nbviewer`:
> * Go to [nbviewer.jupyter.org](https://nbviewer.jupyter.org/)
> * Paste the github link to the notebook.
> 
> Or, say the github link to the notebook is `https://github.com/userxyz/xyz`, then go to the URL: `https://nbviewer.jupyter.org/github/userxyz/xyz`. If the notebook is not rendered like it should, add the parameter `?flush_cache=true` to the end of the URL.

## Single Objective Optimization: PSO and GA (Clustered and Randomized)
Testing Clustered and Randomized populations in PSO and GA on benchmark test functions.
- [[1]](benchmark_ga.ipynb) GA with Randomized population
- [[2]](benchmark_ga_clustered.ipynb) GA with clustered population
- [[3]](benchmark_pso.ipynb) PSO with Randomized population
- [[4]](benchmark_pso_clustered.ipynb) PSO with clustered population

### Comparison of performance:
PSO:
- Overall, more optimal solution compared to GA, except when a function is both parabolic and has several local minima.
- Local search is generally better (optimality and speed) in case of narrow valley functions, but global better if the valley is wide, although slower.
- Local clustered and Global perform similarly in the presence of several local minima (speed and optimality). Speed may differ depending on the valley, if any. 
- Overall, very similar performance of global and local search, with local search slightly faster on average.

GA:
- In parabolic/valley-like functions, GA sees a sudden drop and faster convergence than PSO, but not as optimal as PSO.
- Overall, worse off than PSO in terms of minimization and speed when a function has several local minima. 
- Local (clustered) GA performs better (minimization and speed) when several local minima in a parabolic function. 
- Overall, local and global searches perform similarly.
- Global search dwells in one place in wider parabolic functions but converges faster and is more optimal. Local search better in narrower parabolas.

But these are very vague comparisons, not quantified.

### Additional Comparison technique 
Taken from: [Best practices for comparing optimization algorithms](https://doi.org/10.1007/s11081-017-9366-1)   
> Classifying optimisation methods as “competitive” or “very competitive” (or not competitive at all): First mark convergence times as competitive (Ts <= 2Tmin) or very competitive  (Ts <= (4/3)Tmin) where Ts is the solving time and Tmin is the minimum solving time of over all optimization methods run for a particular problem. After this, the method is rated by measuring the percentage of competitive and very competitive performances of the method. 

Tried: 4 methods, 5 problems

**Time to solve (s):**

Test Problem | PSO | PSO Local | GA | GA Local | Tmin |  
-------------|-----|-----------|----|----------|------| 
Ackley | 0.8864 | 0.8811 | 1.0124 | 1.7519 | 0.8811 |  
Rastrigin | 0.7213 | 0.8445 | 0.8363 | 0.8142 | 0.7213 |  
Rosenbrock | 1.6173 | 4.4754 | 0.9433 | 0.6958 | 0.6958 |  
Griewank | 2.3548 | 0.9290 | 0.4285 | 0.4410 | 0.4285 |   
Zakharov | 0.6658 | 0.4637 | 0.3989 | 0.8769 | 0.3989 |   

**Competitiveness:**

Test | PSO | PSO Local | GA | GA Local | 2Tmin | 4/3 Tmin |  
---|-------|----------|----|--------|-------|--------|  
Ackley | Very | Very | Very | Competitive | 1.7622 | 1.1748 |  
Rastrigin | Very | Very | Very | Very |1.4426 | 0.9617|  
Rosenbrock | Not | Not | Competitive | Very | 1.3916 | 0.9277 |  
Griewank | Not | Not | Very | Very | 0.8570 | 0.5713 |  
Zakharov | Competitive | Very | Very | Not | 0.7978 | 0.5319 |  

**Percentage Competitiveness:**

____| PSO | PSO Local | GA | GA Local |  
---|---|--------|-----|-----|  
Very Competitive | 40% | 60% | 80% | 60% |  
Competitive | 20% | 0% | 20% | 20% |  



### Applications in Engineering:
- [[1]](PSO-Concrete.ipynb) Single Objective PSO for Civil Engineering based on [this paper](http://www.ijimt.org/vol10/832-CM0015.pdf)
- [[2]](GA_Concrete.ipynb) Single Objective GA for Civil Engineering, based on the same paper as above.
- [[3]](structural_design_1_nsga2.ipynb) Structural design solution for a constrained problem: optimal Design of a Pressure Vessel, using NSGA II. Problem 1 (4.2.1) in [this paper](https://www.aimsciences.org/article/exportPdf?id=0b2c367b-f5d5-4214-9b55-fbde31e3b7ad)
- [[4]](structural_design_3_nsga2.ipynb) Structural design solution for a contrained problem: optimal Tension/Compression String Design using, using NSGA II. Problem 3 (4.2.3) in the same paper as above.
- [[5]](clustered_design_1.ipynb) Structural design solution for a constrained problem: optimal Design of a Pressure Vessel, using NSGAII and Clustered population. Problem 1 (4.2.1) in the same paper as above.
- [[6]](clustered_design_3.ipynb) Structural design solution for a contrained problem: optimal Tension/Compression String Design using NSGAII and Clustered population. Problem 3 (4.2.3) in the same paper as above.
- [[7]](struct_design_1_pso.ipynb) Structural design solution for a constrained problem: optimal Design of a Pressure Vessel, using PSO. Problem 1 (4.2.1) in the same paper as above.
- [[8]](struct_design_3_pso.ipynb) Structural design solution for a contrained problem: optimal Tension/Compression String Design, using PSO. Problem 3 (4.2.3) in the same paper as above.
- [[9]](clustered_design_1_pso.ipynb) Structural design solution for a constrained problem: optimal Design of a Pressure Vessel, using PSO and Clustered population. Problem 1 (4.2.1) in the same paper as above.
- [[10]](structural_design_1_ga.ipynb) Structural design solution for a constrained problem: optimal Design of a Pressure Vessel, using GA. Problem 1 (4.2.1) in the same paper as above.
- [[11]](structural_design_3_ga.ipynb) Structural design solution for a contrained problem: optimal Tension/Compression String Design, using GA. Problem 3 (4.2.3) in the same paper as above.
- [[12]](clustered_design_1_ga.ipynb) Structural design solution for a constrained problem: optimal Design of a Pressure Vessel, using GA and Clustered population. Problem 1 (4.2.1) in the same paper as above.
- [[13]](clustered_design_3_ga.ipynb) Structural design solution for a contrained problem: optimal Tension/Compression String Design using GA and Clustered population. Problem 3 (4.2.3) in the same paper as above.
