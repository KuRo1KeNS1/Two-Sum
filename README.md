# Two-Sum
Practice
#include<iostream>
#include<vector>

using std::cin;
using std::cout;
using std::endl;
using std::vector;

class Solution {
public:
	Solution() = default;
	Solution(vector<int> n) :
		nums(n) { }
	vector<int> twoSum(vector<int>& nums, int target) {
		vector<int> ret;
		int k, l;
		vector<int>::const_iterator i, j;
		for ( i = nums.cbegin(), k = 0; i != nums.cend() - 2; i++, k++)
		{
			for ( j = nums.cbegin() + 1 + k, l = k + 1; j != nums.cend() - 1; j++, l++)
			{
				if (*i + *j == target)
				{
					ret.push_back(k);
					ret.push_back(l);
					sign = 1;
					break;
				}
			}
			if (sign == 1)
				break;
		}
		return ret;
	}
	int Getsign() { return sign; }
	vector<int>& Getnums() 
	{ 
		vector<int>& n = nums;
		return n;
	}
	int Gettarget() 
	{
		vector<int>::const_iterator i = nums.cend();
		int target = *(--i);
		return target; 
	}
private:
	vector<int> nums;
	int sign = 0;
};

int main()
{
	vector<int> num, result;
	int temp;

	cout << "Please enter an array of integers and a specific target" << endl;
	cout << "(The last is the specific target, \"e\" to end input):" << endl;

	while (cin >> temp)
		num.push_back(temp);

	Solution ex(num);
	result = ex.twoSum(ex.Getnums(), ex.Gettarget());

	if (ex.Getsign() == 1)
	{
		cout << "The solution is : ";
			for (int i = 0; i != 2; i++)
				cout << result[i] << " ";
		cout << endl;
	}
	else
		cout << "No suitable solution!" << endl;

	return 0;
}
