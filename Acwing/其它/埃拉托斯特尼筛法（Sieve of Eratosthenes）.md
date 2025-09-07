### **埃拉托斯特尼筛法（Sieve of Eratosthenes）**

实现快速筛素数

```c++
#include <iostream>
#include <vector>
#include <cmath>

// 函数功能：使用埃拉托斯特尼筛法找出所有小于n的素数
// 参数：n - 上限值
// 返回值：小于n的素数的数量
int sieveOfEratosthenes(int n) {
    // 处理特殊情况
    if (n <= 2) {
        return 0;
    }
    
    // 创建布尔向量，标记数字是否为素数
    // prime[i]为true表示i是素数
    std::vector<bool> prime(n, true);
    
    // 0和1不是素数
    prime[0] = prime[1] = false;
    
    // 遍历到sqrt(n)即可，因为大于sqrt(n)的因子会成对出现
    for (int i = 2; i <= std::sqrt(n); ++i) {
        // 如果i是素数，则标记其所有倍数为非素数
        if (prime[i]) {
            // 从i*i开始标记，因为更小的倍数已经被标记过了
            for (int j = i * i; j < n; j += i) {
                prime[j] = false;
            }
        }
    }
    
    // 统计并输出所有素数
    int count = 0;
    std::cout << "小于" << n << "的素数有：";
    for (int i = 2; i < n; ++i) {
        if (prime[i]) {
            std::cout << i << " ";
            count++;
        }
    }
    std::cout << std::endl;
    
    return count;
}

int main() {
    int n;
    std::cout << "请输入一个整数n：";
    std::cin >> n;
    
    int primeCount = sieveOfEratosthenes(n);
    std::cout << "小于" << n << "的素数共有" << primeCount << "个" << std::endl;
    
    return 0;
}

```

