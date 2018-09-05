# 알고리즘

[TOC]



### 이진 검색 알고리즘 (Binary Search Algorithm)

특정 범위 내에서 특정 조건에 맞는 '기준값'을 찾아나가는 방식. '기준값'과 범위 내의 '정중앙 값'을 비교하여, 범위 내에 있는 기준값과 일치하지 않는 값을 모두 버린다. 비교값이 틀릴 때마다 값의 범위를 반으로 줄이는 것이기 때문에 순차 검색보다 더 효율적이다. 순차 검색 알고리즘 (Linear Search Algorithm)은 n개의 요소가 있는 배열에서 특정 조건에 맞는 값을 찾기 위해 최대 n번을 탐색해야한다. 

이를 도식화 한 것은 2를 밑으로 하는 로그다. 범위 내에 n개의 항목이 있다면 추측의 수는 최대 log(n) + 1다.  

ex) 32개 요소가 있는 배열에서 특정 요소를 찾기 위해선 최대 5회 추측해야 한다. log2(32) (32가 나오려면 2의 5승이므로.. 5회다. 

*** 로그의 개념 공부 더 필요







######  targetValue가 100 아래의 소수라면 몇 번째인지 반환 & 소수가 아니라면 - 1 반환

```
var doSearch = function(array, targetValue) {
    var min = 0;
    var max = array.length - 1;
   var guess;

   while(max>=min){
       guess = Math.floor( (max+min)/2 );
       if( array[guess] === targetValue ){
           return guess;
       } else if( array[guess] < targetValue ) {
           min = guess + 1;
       } else {
           max = guess - 1;
       }
   }

    return -1;
};

var primes = [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37,
        41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97];

var result = doSearch(primes, 73);
println(“Found prime at index ” + result);

Program.assertEqual(doSearch(primes, 73), 20);
```





### 재귀 알고리즘 (Recursive Algorithm)

- 어떤 문제를 해결하려고 할 때, 동일한 문제의 더 작은 경우를 해결함으로써 그 문제를 해결하는 것. 복잡한 문제를 쪼개고 쪼개서 즉시 풀 수 있는 문제로 작아지게 만든다. 

- 모든 recursion은 iteration으로 변경할 수 있다. ( 참고 https://stackoverflow.com/questions/931762/can-every-recursion-be-converted-into-iteration

모든 트리구조는 recursion으로 변경할 수 있다.



###### 재귀 팩토리얼

```
var factorial = function(n) {
	// base case: 
	if (n === 0) {
	    return 1;
	}
	    return factorial(n-1) * n;
}; 

println("The value of 0! is " + factorial(0) + ".");
println("The value of 5! is " + factorial(5) + ".");

Program.assertEqual(factorial(0), 1);
Program.assertEqual(factorial(5), 120);
```

###### 재귀를 활용해 문자열의 회문인지 확인

```
 // Returns the first character of the string str
var firstCharacter = function(str) {
    return str.slice(0, 1);
};

// Returns the last character of a string str
var lastCharacter = function(str) {
    return str.slice(-1);
};

// Returns the string that results from removing the first
//  and last characters from str
var middleCharacters = function(str) {
    return str.slice(1, -1);
};

var isPalindrome = function(str) {
    if (str.length === 0 || str.length === 1) {
        return true;
    } else if (firstCharacter(str) !== lastCharacter(str)) {
        return false;
    } else {
        return isPalindrome(middleCharacters(str));
    }
};

var checkPalindrome = function(str) {
    println("Is this word a palindrome? " + str);
    println(isPalindrome(str));
};

checkPalindrome("a");
Program.assertEqual(isPalindrome("a"), true);
checkPalindrome("motor");
Program.assertEqual(isPalindrome("motor"), false);
checkPalindrome("rotor");
Program.assertEqual(isPalindrome("rotor"), true);
```

###### 재귀를 활용해 x의 n승을 확인 

```
var isEven = function(n) {
    return n % 2 === 0;
};

var isOdd = function(n) {
    return !isEven(n);
};

var power = function(x, n) {
    println("Computing " + x + " raised to power " + n + ".");
    // base case
    if (x === 1 || n === 0) {
        return 1;
    } else if ( n > 0 && isOdd(n) ) {
        return x * power(x, n-1);
    } else if ( n > 0 && isEven(n) ) {
        var y = power(x, n/2);
        return y * y;
    } else if ( n < 0 ) {
        return 1/power(x, -(n));
    }
};  

var displayPower = function(x, n) {
    println(x + " to the " + n + " is " + power(x, n));
};

displayPower(3, 0);
Program.assertEqual(power(3, 0), 1);
displayPower(3, 1);
Program.assertEqual(power(3, 1), 3);
displayPower(3, 2);
Program.assertEqual(power(3, 2), 9);
displayPower(3, -1);
Program.assertEqual(power(3, -1), 1/3);
displayPower(4, -2);
Program.assertEqual(power(4, -2), 1/16);
displayPower(5, 5);
Program.assertEqual(power(5, 5), 3125);
```



### Fisher-Yates Shuffle

유한한 숫자로 랜덤 순열을 만드는 알고리즘. 쉽게 말해 랜덤한 숫자 뽑을 때 쓴다. 이름은 이를 고안한 Ronald Fisher와 Frank Yates에서 따왔다. 모든 요소를 모자에 넣고 모자에 아무런 요소가 남아있지 않을 때까지 랜덤하게 요소를 빼낸다. 







