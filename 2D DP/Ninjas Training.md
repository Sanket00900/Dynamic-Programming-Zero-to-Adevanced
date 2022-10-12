

1. Recursion

```
    public static int ninjaTraining(int n, int points[][]) {
        return helper(n-1,points,3);
    }
    
    private static int helper(int day,int points[][],int task){
        if(day == 0){
            int max = 0;
            for(int i=0; i < 3; i++){
                if(i != task){
                    max = Math.max(max,points[0][i]);
                }        
            }
        }
        
        int maxi = 0;
        for(int i=0; i < 3; i++){
            if(i != task){
                int activity = points[day][i] + helper(day - 1, points,i);
                maxi = Math.max(maxi,activity);
            }
        }
        return maxi;
    }
```

2. Memoization 

```
    public static int ninjaTraining(int n, int points[][]) {
        int[][]dp = new int[n][4];
        return helper(n-1,3 ,points,dp);
    }
    
    private static int helper(int day,int last,int points[][],int[][]dp){
        if(dp[day][last] != 0) return dp[day][last];

        if (day == 0) {
            int maxi = 0;
            for (int i = 0; i <= 2; i++) {
                if (i != last)
                    maxi = Math.max(maxi, points[0][i]);
            }
            return dp[day][last] = maxi;
        }

        int maxi = 0;
        for (int i = 0; i <= 2; i++) {
            if (i != last) {
                int activity = points[day][i] + helper(day - 1, i, points, dp);
                maxi = Math.max(maxi, activity);
            }
        }
        return dp[day][last] = maxi;
    }
```
