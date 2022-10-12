1. Recursion 
 ```
    public int climbStairs(int n){
       if(n <= 1) return 1;
       return climbStairs(n-1) + climbStairs(n-2);
    }
```

2. Memoization 
  
```
    public int climbStairs(int n){
        return climbStairs(n, new int [n+1]);
    }
    
    private int climbStairs(int n, int[]dp){
        if(n <= 1) return 1;
        if(dp[n] != 0) return dp[n];
        return dp[n] = climbStairs(n-1,dp) + climbStairs(n-2,dp);
    }
```    

3. Tabulation 

```
    public int climbStairs(int n){
        if(n==0 || n==1) return 1;
        int[] dp=new int[n+1];
        dp[0]=1;
        dp[1]=1;

        for(int i=2;i<dp.length;i++){
            dp[i]=dp[i-1]+dp[i-2];
        }
    return dp[n];
    }
```

4. Soace Opr=timization 

```
    public int climbStairs(int n){    
        if(n <= 1) return 1;
        int prev2 = 1;
        int prev = 1;
        for(int i = 2; i <= n; i++){
            int curri = prev + prev2;
            prev2 = prev;
            prev = curri;
        }
        return prev;
    }
    
```
