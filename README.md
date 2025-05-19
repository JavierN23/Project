PROJECT

Task 1:

    #include <iostream>
    #include <vector>
    #include <unordered_set>
    #include <string>
    struct Player {
    std::string first_name;
    std::string last_name;
    std::string team;
    };
    std::vector<std::string> findPlayersInBothSports(
    const std::vector<Player>& basketballPlayers, 
    const std::vector<Player>& footballPlayers) 
    {
    std::unordered_set<std::string> basketballNames;
    std::vector<std::string> commonPlayers;
    for (const auto& player : basketballPlayers) {
        std::string fullName = player.first_name + " " + player.last_name;
        basketballNames.insert(fullName);
    }


    for (const auto& player : footballPlayers) {
        std::string fullName = player.first_name + " " + player.last_name;
        if (basketballNames.count(fullName)) {
            commonPlayers.push_back(fullName);
        }
    }

    return commonPlayers;  }
    
    int main() {
    std::vector<Player> basketball_players = {
        {"Jill", "Huang", "Gators"},
        {"Janko", "Barton", "Sharks"},
        {"Wanda", "Vakulskas", "Sharks"},
        {"Jill", "Moloney", "Gators"},
        {"Luuk", "Watkins", "Gators"}
        };
    std::vector<Player> football_players = {
        {"Hanzla", "Radosti", "32ers"},
        {"Tina", "Watkins", "Barleycorns"},
        {"Alex", "Patel", "32ers"},
        {"Jill", "Huang", "Barleycorns"},
        {"Wanda", "Vakulskas", "Barleycorns"}
    };
    std::vector<std::string> result = findPlayersInBothSports(basketball_players, football_players);
    std::cout << "Players in both sports:\n";
    for (const auto& name : result) {
        std::cout << name << std::endl;
    }
    return 0;
    }
Task 2:

    #include <iostream>
    #include <vector>
    using namespace std;

    int missingNum(const vector<int>& arr) {
    int n = arr.size();  


    int expectedSum = n * (n + 1) / 2;

    int actualSum = 0;
    for (int num : arr) {
        actualSum += num;
    }


    return expectedSum - actualSum;
    }

    int main() {
    vector<int> arr = {8, 2, 3, 9, 4, 7, 5, 0, 6};
    cout << missingNum(arr) << endl; 

    vector<int> arr2 = {1, 2, 3, 4, 5};
    cout << missingNum(arr2) << endl; 

    vector<int> arr3 = {0, 1, 2, 3, 4, 5};
    cout << missingNum(arr3) << endl; 

    return 0;
    }

Task 3:

    #include <iostream>
    #include <vector>
    using namespace std;

    int maxProfit(const vector<int>& prices) {
    if (prices.size() < 2) return 0;

    int minPriceSoFar = prices[0];
    int bestProfit = 0;

    for (int price : prices) {
       
        if (price > minPriceSoFar) {
            int profit = price - minPriceSoFar;
            if (profit > bestProfit) {
                bestProfit = profit;
            }
        } else {
                   minPriceSoFar = price;
        }
    }

    return bestProfit;
    }

    int main() {
    vector<int> prices = {10, 7, 5, 8, 11, 2, 6};
    cout << "Max profit: $" << maxProfit(prices) << endl;
    return 0;
    }

Task 4:

    #include <iostream>
    #include <vector>
    #include <algorithm>
    using namespace std;

    int highestProductOfTwo(vector<int> nums) {
    sort(nums.begin(), nums.end());

    int n = nums.size();

   
    int product1 = nums[n-1] * nums[n-2];

   
    int product2 = nums[0] * nums[1];

    return max(product1, product2);
    }

    int main() {
    vector<int> nums = {5, -10, -6, 9, 4};
    cout << highestProductOfTwo(nums) << endl;
    return 0;
    }

Task 5:

    #include <iostream>
    #include <vector>
    using namespace std;

    vector<double> countingSortTemps(const vector<double>& temps) {
    double start = 97.0;
    double end = 99.0;
    double step = 0.1;

    int size = (int)((end - start) / step) + 1;

    vector<int> counts(size, 0);
    for (double temp : temps) {
        int idx = (int)((temp - start) / step);
        counts[idx]++;
    }
    vector<double> sorted;
    for (int i = 0; i < size; i++) {
        double val = start + i * step;
        for (int j = 0; j < counts[i]; j++) {
            sorted.push_back(val);
        }
    }

    return sorted;
    }

    int main() {
    vector<double> temps = {98.6, 98.0, 97.1, 99.0, 98.9, 97.8, 98.5, 98.2, 98.0, 97.1};

    vector<double> sortedTemps = countingSortTemps(temps);

    for (double temp : sortedTemps) {
        cout << temp << " ";
    }
    cout << endl;

    return 0;
    }

Task 6:

    #include <iostream>
    #include <unordered_set>
    #include <vector>
    using namespace std;

    int longestConsecutive(const vector<int>& nums) {
    unordered_set<int> numSet(nums.begin(), nums.end());
    int longestStreak = 0;

    for (int num : nums) {
        if (numSet.find(num - 1) == numSet.end()) {
            int currentNum = num;
            int currentStreak = 1;

            while (numSet.find(currentNum + 1) != numSet.end()) {
                currentNum++;
                currentStreak++;
            }

            if (currentStreak > longestStreak)
                longestStreak = currentStreak;
        }
    }

    return longestStreak;
    }

    int main() {
    vector<int> nums = {10, 5, 12, 3, 55, 30, 4, 11, 2};
    cout << "Longest consecutive sequence length: " << longestConsecutive(nums) << endl;

    vector<int> nums2 = {19, 13, 15, 12, 18, 14, 17, 11};
    cout << "Longest consecutive sequence length: " << longestConsecutive(nums2) << endl;

    return 0;
    }
