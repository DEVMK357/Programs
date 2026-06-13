import java.util.*;

class Solution {
    public int[] exclusiveTime(int n, List<String> logs) {
        int[] ans = new int[n];
        Stack<Integer> st = new Stack<>();
        int prev = 0;

        for (String log : logs) {
            String[] p = log.split(":");
            int id = Integer.parseInt(p[0]);
            int time = Integer.parseInt(p[2]);

            if (p[1].equals("start")) {
                if (!st.isEmpty()) ans[st.peek()] += time - prev;
                st.push(id);
                prev = time;
            } else {
                ans[st.pop()] += time - prev + 1;
                prev = time + 1;
            }
        }
        return ans;
    }
}
