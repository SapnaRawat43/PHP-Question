class Solution {
    /**
     * @param Integer $n
     * @return Boolean
     */
    function isHappy($n) {
       $seen = [];
        while ($n != 1) {
            // If we've seen this number before, it's a cycle
            if (isset($seen[$n])) {
                return false;
            }

            // Mark the current number as seen
            $seen[$n] = true;

            // Calculate the sum of the squares of its digits
            $n = $this->sumOfSquares($n);
        }

        return true;
    }

    // calculate the sum of the squares of digits
    private function sumOfSquares($n) {
        $sum = 0;

        while ($n > 0) {
            $digit = $n % 10;
            $sum += $digit * $digit;
            $n = (int)($n / 10);
        }

        return $sum;
    }
}
