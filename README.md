#include <stdio.h>
#include <stdbool.h>

// function to check if a number is prime
bool is_prime(int num) {
    if (num <= 1) {
        return false;
    }
    for (int i = 2; i <= num/2; i++) {
        if (num % i == 0) {
            return false;
        }
    }
    return true;
}

int main() {
    int start, end;
    printf("Enter the starting number: ");
    scanf("%d", &start);
    printf("Enter the ending number: ");
    scanf("%d", &end);
    printf("Prime numbers between %d and %d are: ", start, end);
    for (int i = start; i <= end; i++) {
        if (is_prime(i)) {
            printf("%d ", i);
        }
    }
    return 0;
}







#include <stdio.h>
int checkPrime(int n);
int main() {
  int n, i, flag = 0;
  printf("Enter a positive integer: ");
  scanf("%d", &n);

  for (i = 2; i <= n / 2; ++i) 
  {
    if (checkPrime(i) == 1) {
      if (checkPrime(n - i) == 1) {
        printf("%d = %d + %d\n", n, i, n - i);
        flag = 1;
      }
    }
  }

  if (flag == 0)
    printf("%d cannot be expressed as the sum of two prime numbers.", n);

  return 0;
}

int checkPrime(int n) 
{
  int i, isPrime = 1;
  if (n == 0 || n == 1) 
  {
    isPrime = 0;
  }
  else 
  {
    for(i = 2; i <= n/2; ++i) 
	{
      if(n % i == 0) 
	  {
        isPrime = 0;
        break;
      }
    }
  }

  return isPrime;
}





#include <stdio.h>
int findGCD(int num1, int num2) {
    if(num2 == 0) {
        return num1;
    } else {
        return findGCD(num2, num1 % num2);
    }
}
int main() {
    int num1, num2, gcd;
    printf("Enter two numbers: ");
    scanf("%d %d", &num1, &num2);
    gcd = findGCD(num1, num2);
    printf("The GCD of %d and %d is %d", num1, num2, gcd);
    return 0;
}






#include <stdio.h>

int main() {

    int n1, n2, max;

    printf("Enter two positive integers: ");
    scanf("%d %d", &n1, &n2);

    max = (n1 > n2) ? n1 : n2;

    while (1) {
        if ((max % n1 == 0) && (max % n2 == 0)) {
            printf("The LCM of %d and %d is %d.", n1, n2, max);
            break;
        }
        ++max;
    }
    return 0;
}







#include <stdio.h>
#include <string.h>

char string1[100], visited[100];
int count[100] = {0}, flag = 0;

void main()
{
    int i, j = 0, k = 0, l, max, index;

    printf("Enter a string : ");
    scanf("%[^\n]s", string1);

    l = strlen(string1);

    for (i = 0; i < l; i++)
    {
        if (i == 0)
        {
            visited[j++] = string1[i];
            count[j - 1]++;
        }
        else
        {
            for (k = 0; k  < j; k++)
            {
                if (string1[i] == visited[k])
                {
                    count[k]++;
                    flag = 1;
                }
            }
            if (flag == 0)
            {
                visited[j++] = string1[i];
                count[j - 1]++;
            }
            flag = 0;
        }
    }    

    for (i = 0; i < j; i++)
    {
        if ((i == 0) && (visited[i] != ' '))
        {
            max = count[i];
            continue;
        }
        if ((max < count[i]) && (visited[i] != ' '))
        {
            max = count[i];
            index = i;
        }
    }

    printf("\nMax repeated character in the string = %c ", visited[index]);
    printf("\nIt occurs %d times", count[index]);
}









@@ -0,0 +1,43 @@
#include <stdio.h>

int find_anagram(char [], char []);

int main()
{
    char array1[100], array2[100];
    int flag;

    printf("Enter the string\n");
    gets(array1);
    printf("Enter another string\n");
    gets(array2);
    flag = find_anagram(array1, array2);
    if (flag == 1)
        printf("%s and %s are anagrams.\n", array1, array2);
    else
        printf(" %s and %s are not anagrams.\n", array1, array2);
    return 0;
}

int find_anagram(char array1[], char array2[])
{
    int num1[26] = {0}, num2[26] = {0}, i = 0;

    while (array1[i] != '\0')
    {
        num1[array1[i] - 'a']++;
        i++;
    }
    i = 0;
    while (array2[i] != '\0')
    {
        num2[array2[i] -'a']++;
        i++;
    }
    for (i = 0; i < 26; i++)
    {
        if (num1[i] != num2[i])
            return 0;
    }
    return 1;
}








#include <stdio.h>
#include <string.h>

void main()
{
    int sum = 0, i, len;
    char string1[100];

    printf("Enter the string : ");
    scanf("%[^\n]s", string1);
        len = strlen(string1);
    for (i = 0; i < len; i++)
    {
        sum = sum + string1[i];
    }
    printf("\nSum of all characters : %d ",sum);
}







#include <stdio.h>

int main()
{

	int a[5] = { 45, 22, 100, 66, 37 };
	int n = 5, i, j, t = 0;

	// iterates the array elements
	for (i = 0; i < n; i++) {

		// iterates the array elements from index 1
		for (j = i + 1; j < n; j++) {

			// comparing the array elements, to set array
			// elements in descending order
			if (a[i] < a[j]) {
				t = a[i];
				a[i] = a[j];
				a[j] = t;
			}
		}
	}
	// printing the output
	for (i = 0; i < n; i++) {
		printf("%d ", a[i]);
	}
	return 0;
}



#include <stdio.h>
#include <string.h>
void reverseString(char* str)
{
	int l, i;
	char *begin_ptr, *end_ptr, ch;
	l = strlen(str);
	begin_ptr = str;
	end_ptr = str + l - 1;
	for (i = 0; i < (l - 1) / 2; i++) 
	{
		ch = *end_ptr;
		*end_ptr = *begin_ptr;
		*begin_ptr = ch;
		begin_ptr++;
		end_ptr--;
	}
}


int main()
{

	char str[100] = "GeeksForGeeks";
	printf("Enter a string: %s\n", str);
	reverseString(str);
	printf("Reverse of the string: %s\n", str);

	return 0;
}
