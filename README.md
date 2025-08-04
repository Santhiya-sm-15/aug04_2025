# aug04_2025
The problem that i solved today in leetcode

You are visiting a farm that has a single row of fruit trees arranged from left to right. The trees are represented by an integer array fruits where fruits[i] is the type of fruit the ith tree produces.

You want to collect as much fruit as possible. However, the owner has some strict rules that you must follow:

You only have two baskets, and each basket can only hold a single type of fruit. There is no limit on the amount of fruit each basket can hold.
Starting from any tree of your choice, you must pick exactly one fruit from every tree (including the start tree) while moving to the right. The picked fruits must fit in one of your baskets.
Once you reach a tree with fruit that cannot fit in your baskets, you must stop.
Given the integer array fruits, return the maximum number of fruits you can pick.

Code:
class Solution {
    public int totalFruit(int[] fruits) {
        int n=fruits.length;
        Map<Integer,Integer> m=new HashMap<>();
        int l=0,r=0,max=0;
        while(r<n)
        {
            m.put(fruits[r],m.getOrDefault(fruits[r],0)+1);
            while(m.size()>2)
            {
                if(m.get(fruits[l])==1)
                    m.remove(fruits[l]);
                else
                    m.put(fruits[l],m.get(fruits[l])-1);
                l++;
            }
            max=Math.max(max,r-l+1);
            r++;
        }
        return max;
    }
}
