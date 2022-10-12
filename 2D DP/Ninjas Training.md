

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
