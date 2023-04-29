# Shor's Algorithm

This code provides an implementation of the Shor's algorithm using the Amazon Braket SDK. Shor's algorithm is used to find prime factors of an integer. On a quantum computer, Shor's algorithm runs in polynomial time and is almost exponentially faster than the most efficient known classical factoring algorithm. The efficiency of Shor's algorithm is due to the efficiency of the Quantum Fourier transform, Quantum Phase estimation and modular exponentiation by repeated squarings. In this notebook, you implement the Shor's algorithm in code using the Amazon Braket SDK and run a simple example of factoring 15.

# References 

[1] Wikipedia: https://en.wikipedia.org/wiki/Shor%27s_algorithm

[2] Nielsen, Michael A., Chuang, Isaac L. (2010). Quantum Computation and Quantum Information (2nd ed.). Cambridge: Cambridge University Press.


```python
from braket.devices import LocalSimulator
from braket.aws import AwsDevice
from braket.experimental.algorithms.shors.shors import (
    shors_algorithm,
    run_shors_algorithm,
    get_factors_from_results
)

```

# Prepare inputs for Shor's Algorithm


```python
N = 15 # Integer to factor 
a = 7  # Any integer that satisfies 1 < a < N and gcd(a, N) = 1.


shors_circuit = shors_algorithm(N, a)
```

# Run on a local simulator


```python
local_simulator = LocalSimulator()

output = run_shors_algorithm(shors_circuit, local_simulator)

guessed_factors = get_factors_from_results(output, N, a)

```

    Number of Measured phases (s/r) : 4
    
    For phase 0.0 :
    Estimate for r is : 1
    Factors are : 15 and 1
    
    For phase 0.25 :
    Estimate for r is : 4
    Factors are : 3 and 5
    
    For phase 0.75 :
    Estimate for r is : 4
    Factors are : 3 and 5
    
    For phase 0.5 :
    Estimate for r is : 2
    Factors are : 3 and 1
    
    
    Non-trivial factors found are : {3, 5}


# Run on a Quantum Computing Device (Rigetti's Aspen-M-3)

Rigetti 양자 프로세서는 튜닝 가능한 초전도 큐비트를 기반으로 하는 범용 게이트 모델 머신입니다. Rigetti의 최신 Aspen-M 프로세서는 확장 가능한 다중 칩 기술을 기반으로 하며, 깊이와 넓이에 관계없이 전반적인 회로 충실도를 높이는 향상된 판독 기능을 갖추고 있습니다. Aspen M 시스템은 빠른 처리 시간, 각종 얽힘 게이트의 빠른 적용, 액티브 레지스터 재설정을 통한 빠른 샘플링, 그리고 파라메트릭 제어 기능을 포함합니다. Aspen 칩 토폴로지는 큐비트를 3중(가장자리에서는 2중)으로 연결한 8각형 구조이며, 개발자가 성능 향상을 위해 프로그램을 최적화하고 회로 깊이를 최소화할 수 있도록 CPHASE 및 XY 연결 게이트를 모두 지원하고 있습니다. Rigetti의 최적화 컴파일러 quil-c는 추상적인 양자 알고리즘을 Rigetti QPU에서 동작하는 네이티브 게이트들로 재구성하고 최적화된 회로 구현을 생성합니다. 이 게이트들은 큐비트 결맞음 시간(T1은 28µs, T2는 22µs) 내에 프로그램을 구동할 수 있도록 빠른 1Q 및 2Q 실행 시간(각각 40ns 및 220ns)을 제공합니다.

- 하드웨어 공급자: Rigetti
- 위치: California, USA
- 큐비트: 79
- 펄스 제어: 지원됨


```python
from braket.tracking import Tracker
tracker = Tracker().start()
```


```python
managed_sim = AwsDevice("arn:aws:braket:us-west-1::device/qpu/rigetti/Aspen-M-3")

output = run_shors_algorithm(shors_circuit, managed_sim)

guessed_factors = get_factors_from_results(output, N, a)
```

    Number of Measured phases (s/r) : 16
    
    For phase 0.0625 :
    Estimate for r is : 15
    Factors are : 3 and 1
    
    For phase 0.875 :
    Estimate for r is : 8
    Factors are : 15 and 1
    
    For phase 0.75 :
    Estimate for r is : 4
    Factors are : 3 and 5
    
    For phase 0.5 :
    Estimate for r is : 2
    Factors are : 3 and 1
    
    For phase 0.25 :
    Estimate for r is : 4
    Factors are : 3 and 5
    
    For phase 0.0 :
    Estimate for r is : 1
    Factors are : 15 and 1
    
    For phase 0.8125 :
    Estimate for r is : 11
    Factors are : 3 and 1
    
    For phase 0.5625 :
    Estimate for r is : 9
    Factors are : 15 and 1
    
    For phase 0.4375 :
    Estimate for r is : 9
    Factors are : 15 and 1
    
    For phase 0.375 :
    Estimate for r is : 8
    Factors are : 15 and 1
    
    For phase 0.3125 :
    Estimate for r is : 13
    Factors are : 3 and 5
    
    For phase 0.125 :
    Estimate for r is : 8
    Factors are : 15 and 1
    
    For phase 0.1875 :
    Estimate for r is : 11
    Factors are : 3 and 1
    
    For phase 0.625 :
    Estimate for r is : 8
    Factors are : 15 and 1
    
    For phase 0.6875 :
    Estimate for r is : 13
    Factors are : 3 and 5
    
    For phase 0.9375 :
    Estimate for r is : 15
    Factors are : 3 and 1
    
    
    Non-trivial factors found are : {3, 5}



```python
print("Task Summary")
print(f"{tracker.quantum_tasks_statistics()} \n")
print(f"Estimated cost to run this example: {tracker.qpu_tasks_cost() + tracker.simulator_tasks_cost():.2f} USD")
```

    Task Summary
    {'arn:aws:braket:us-west-1::device/qpu/rigetti/Aspen-M-3': {'shots': 1000, 'tasks': {'COMPLETED': 1}}} 
    
    Estimated cost to run this example: 0.65 USD


    Task is in terminal state FAILED and no result is available.
    Task failure reason is: Failed to compile task; Timeout on device Aspen-M-3; Unable to complete Rigetti compilation; the circuit may be too large.


Note: Charges shown are estimates based on your Amazon Braket simulator and quantum processing unit (QPU) task usage. Estimated charges shown may differ from your actual charges. Estimated charges do not factor in any discounts or credits, and you may experience additional charges based on your use of other services such as Amazon Elastic Compute Cloud (Amazon EC2).
