# Permutations-of-a-String--gfg
Given a string s, which may contain duplicate characters, your task is to generate and return an array of all unique permutations of the string. You can return your answer in any order.

Examples:

Input: s = "ABC"
Output: ["ABC", "ACB", "BAC", "BCA", "CAB", "CBA"]
Explanation: Given string ABC has 6 unique permutations.
Input: s = "ABSG"
Output: ["ABGS", "ABSG", "AGBS", "AGSB", "ASBG", "ASGB", "BAGS", "BASG", "BGAS", "BGSA", "BSAG", "BSGA", "GABS", "GASB", "GBAS", "GBSA", "GSAB", "GSBA", "SABG", "SAGB", "SBAG", "SBGA", "SGAB", "SGBA"]
Explanation: Given string ABSG has 24 unique permutations.
Input: s = "AAA"
Output: ["AAA"]
Explanation: No other unique permutations can be formed as all the characters are same.

## code c++
#include <iostream>
#include <unordered_set>
#include <vector>
#include <string>
using namespace std;

class Solution {
public:
    vector<string> findPermutation(string s) {
        
        unordered_set<string> uniquePermutations;

        
        permute(s, "", uniquePermutations);

       
        vector<string> result(uniquePermutations.begin(), uniquePermutations.end());
        return result;
    }

private:
    void permute(const string &s, const string &prefix, unordered_set<string> &uniquePermutations) {
        
        if (s.empty()) {
            uniquePermutations.insert(prefix);
            return;
        }

        for (size_t i = 0; i < s.length(); i++) {
            
            char current = s[i];
            string remaining = s.substr(0, i) + s.substr(i + 1);

            
            permute(remaining, prefix + current, uniquePermutations);
        }
    }
};

