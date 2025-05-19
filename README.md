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
