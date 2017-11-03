# Two-Sum
Practice
#include<stdlib.h>
#include<iostream>
#include<vector>
#include<algorithm>
#include<functional>

using std::cin;
using std::cout;
using std::endl;
using std::vector;

class Solution {
public:
	Solution() = default;
	Solution(vector<int> n) :
		nums(n) { }
	int ta, re;
	int te = 0;
	vector<int> twoSum(vector<int>& nums, int target) {
		vector<int> ret;
		vector<int> b_nums = nums;
		sort(b_nums.begin(), b_nums.end() - 1);
		int k, l, t;
		int s = 0;
		int m = b_nums.size() - 1;
		vector<int>::const_iterator i, j;
		for (i = b_nums.cbegin(), j = b_nums.cend() - 2; i != j; i++, m--)
		{	
			te++;
			re = target - *i;
			bis(re, m, i + 1, j);
			if (sign == 1)
			{
				ta = *i;
				break;
			} 
		}
		if (sign == 1)
		{
			for (i = nums.cbegin(), t = 0; i != nums.cend() - 1; i++, t++)
			{
				if ((ta == *i) && (s != 1))
				{
					k = t;
					s = 1;
				}
				else if (re == *i)
					l = t;
			}
			int temp;
			if (k > l)
			{
				temp = k;
				k = l;
				l = temp;
			} 
			ret.push_back(k);
			ret.push_back(l);
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
	void bis(int r, int m, vector<int>::const_iterator i, vector<int>::const_iterator j)
	{
		m /= 2;
		if (m != 0)
		{
			if (r < *(i + m))
				bis(r, m, i, i + m - 1);
			else if (r > *(i + m))
				bis(r, m, i + m + 1, j);
			else
				sign = 1;
		}
		else
		{
			if (r == *j)
				sign = 1;
		}
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
