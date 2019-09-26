## 299. Bulls and Cows

#### You are playing the following Bulls and Cows game with your friend: You write down a number and ask your friend to guess what the number is. Each time your friend makes a guess, you provide a hint that indicates how many digits in said guess match your secret number exactly in both digit and position (called "bulls") and how many digits match the secret number but locate in the wrong position (called "cows"). Your friend will use successive guesses and hints to eventually derive the secret number.

Write a function to return a hint according to the secret number and friend's guess, use A to indicate the bulls and B to indicate the cows. 

Please note that both secret number and friend's guess may contain duplicate digits.

#

## Solution

```
class Solution {
    public String getHint(String secret, String guess) {
        char[] secretArr = secret.toCharArray();
        char[] guessArr = guess.toCharArray();
        int n = guessArr.length;
        
        int bull = 0;
        int cow = 0;
        int[] ifBull = new int[n];
        
        for(int i = 0; i < n; i++) {
            if (guessArr[i] == secretArr[i]) {
                bull ++;
                ifBull[i] = 1;
            }
        }
        
        int[] ifCow = ifBull.clone();
        for(int i = 0; i < n; i++) {
            if(ifBull[i] == 0){
                for(int j = 0; j < n; j++){
                    if(i != j && guessArr[i] == secretArr[j] && ifCow[j] == 0) {
                        cow++;
                        ifCow[j] = 1;
                        break;   
                    }
                }
            }
        }
        String result = String.valueOf(bull) + 'A' + String.valueOf(cow) + 'B';
        
        return result;
    }
}
```

#### Notes

##### Find the Bull first (which the number and position are extactly the same), then find the Cow using the second for loop. 