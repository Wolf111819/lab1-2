#include <iostream>
#include <vector>
#include <climits>

int main() {
    // Введення розміру масиву та його елементів
    int n;
    std::cout << "Введіть розмір масиву: ";
    std::cin >> n;

    std::vector<int> arr(n);
    std::cout << "Введіть елементи масиву:\n";
    for (int i = 0; i < n; i++) {
        std::cin >> arr[i];
    }

    // Знаходимо індекс першого нульового елемента
    int zeroIndex = -1;
    for (int i = 0; i < n; i++) {
        if (arr[i] == 0) {
            zeroIndex = i;
            break;
        }
    }

    if (zeroIndex == -1) {
        std::cout << "Немає нульових елементів у масиві.\n";
    } else {
        // Знаходимо перше додатнє число праворуч від нуля та його індекс
        int minPositive = INT_MAX;
        int minPositiveIndex = -1;
        for (int i = zeroIndex + 1; i < n; i++) {
            if (arr[i] > 0) {
                if (arr[i] < minPositive) {
                    minPositive = arr[i];
                    minPositiveIndex = i;
                }
            }
        }

        if (minPositiveIndex == -1) {
            std::cout << "Немає додатніх елементів праворуч від нуля.\n";
        } else {
            std::cout << "Номер першого мінімального додатнього елемента праворуч від нуля: " << minPositiveIndex + 1 << std::endl;
        }
    }

    return 0;
}
