**Solution:**

Let T be the number of useful chocolates that we will distribute to the friends. Clearly T cannot contain more than m chocolates of same type. To understant consider that there are Ci chocolates of type i present in T and Ci > m, then after distributing 1 chocolate of this type to each friend we will be left with (Ci - m) chocolates will not be useful which contradicts our definition of T.

Hence we will calculate the value of T from our box of chocolates. First we count frequency of each type of chocolate (for this we can either use unordered_map or map). Then we initialize our T with 0. Then we go over every chocolate and add min(m, Ci) to T.

Now, let S be the sum of Xj, i.e sum of number of unique chocolates that each friend wants.

Finally, if T >= S, then we can distrubute chocolates in such a way that makes every friend happy. Otherwise, we say it is not possible to make alll friends happy.

```c++
void chocolateDistribution()
{
    // taking input
    long long n, m; 
    cin >> n >> m;
    
    // types of chocolates
    vector<long long> box(n);
    for(int i = 0; i < n; i++)
    {
        cin >> box[i];
    }
    
    // S is sum of number of unique chocolates required for each friend
    long long S = 0;
    for(int i = 0; i < m; i++)
    {
        long long x;
        cin >> x;
        S += x;
    }
    
    // storing the frequency of each type of chocolate
    unordered_map<long long, long long> count;
    for(int i = 0; i < n; i++)
    {
        count[box[i]]++;
    }
    
    // calculating the value of useful chocolates
    long long T = 0;
    for(auto p : count)
    {
        // p.first is the type of chocolate
        // p.second is the frequency of this chocolate
        T += min(m, p.second);
    }
    if(T >= S)
    {
        cout << "YES\n";
    }
    else
    {
        cout << "NO\n";
    }
}
```

