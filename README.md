Mohammed ismail

Technical Test

Problem 1: 

First solution with C#


public static string LongestCommenString(string FirstString,string SecondString){
 var lengths = new int[FirstString.Length, SecondString.Length];
 int greatestLength = 0;
 string output = "";
 
 for (int indexOne = 0; indexOne < FirstString.Length; indexOne++)
 {
 for (int indexTwo = 0; indexTwo < SecondString.Length; indexTwo++)
 {
 if (FirstString[indexOne] == SecondString[indexTwo])
 {
 lengths[indexOne, indexTwo] = indexOne == 0 || indexTwo == 0 ? 1 : lengths[indexOne - 1, indexTwo - 1] + 1;
 if (lengths[indexOne, indexTwo] > greatestLength)
 {
 greatestLength = lengths[indexOne, indexTwo];
 output = FirstString.Substring(indexOne - greatestLength + 1, greatestLength);
 }
 }
 else
 {
 lengths[indexOne, indexTwo] = 0;
 }
 }
 }
 if(output.Length==1)
 return "";
 else
 return output;
 }


Problem 2:

Time complexity is O(N) but in the case of M greater than N will lead to an infinite loop so we should make M less 
than or equal to N to avoid the infinite loop.

Second solution for first problem with javascript :


const longestCommenString= (firstString = '', secondString = '') => {
 const s1 = [...firstString];
 const s2 = [...secondString];
 const arr = Array(s2.length + 1).fill(null).map(() => {
 return Array(s1.length + 1).fill(null);
 });
 for (let indexTwo = 0; indexTwo <= s1.length; indexTwo += 1) {
 arr[0][indexTwo] = 0;
 }
 for (let indexOne = 0; indexOne <= s2.length; indexOne += 1) {
 arr[indexOne][0] = 0;
 }
 let len = 0;
 let col = 0;
 let row = 0;
 for (let indexOne = 1; indexOne <= s2.length; indexOne += 1) {
 for (let indexTwo = 1; indexTwo <= s1.length; indexTwo += 1) {
 if (s1[indexTwo - 1] === s2[indexOne - 1]) {
 arr[indexOne][indexTwo] = arr[indexOne - 1][indexTwo - 1] + 1;
 }
 else {
 arr[indexOne][indexTwo] = 0;
 }
 if (arr[indexOne][indexTwo] > len) {
 len = arr[indexOne][indexTwo];
 col = indexTwo;
 row = indexOne;
 }
 }
 }
 if (len === 0) {
 return '';
 }
 let res = '';
 while (arr[row][col] > 0) {
 res = s1[col - 1] + res;
 row -= 1;
 col -= 1;
 }
 
 if(res.length==1){
 return ''}
 else{
 return res;
 }
}
