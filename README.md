# Leetcode-2379

# C++

class Solution {
public:
    int minimumRecolors(string blocks, int k) {
        int black=0,white=0;
        for(int i=0;i<k;i++)
        {
            if(blocks[i]=='W')white++;
            else black++;
        }
        int ans=white;
        for(int i=k;i<blocks.length();i++)
        {
            if(blocks[i]=='W')white++;
            else black++;
            if(blocks[i-k]=='W')white--;
            else black--;
            ans=min(ans,white);
            //cout<<ans<<"\n";
        }
        return ans;
    }
};

# Java

class Solution {
    public int minimumRecolors(String blocks, int k) {
        int white = 0;

        // Count the number of 'W' in the first k-length window
        for (int i = 0; i < k; i++) {
            if (blocks.charAt(i) == 'W') {
                white++;
            }
        }

        int ans = white;

        // Sliding window approach
        for (int i = k; i < blocks.length(); i++) {
            if (blocks.charAt(i) == 'W') {
                white++;
            }
            if (blocks.charAt(i - k) == 'W') {
                white--;
            }
            ans = Math.min(ans, white);
        }

        return ans;
    }
}

# Python

class Solution:
    def minimumRecolors(self, blocks: str, k: int) -> int:
        white = sum(1 for i in range(k) if blocks[i] == 'W')
        ans = white
        
        for i in range(k, len(blocks)):
            if blocks[i] == 'W':
                white += 1
            if blocks[i - k] == 'W':
                white -= 1
            ans = min(ans, white)
        
        return ans
