Duplicate in an array of N+1 integers in C
Here, in this page we will discuss the program to find the duplicate in an array of N+1 integers in C . We are Given an array of integers Arr containing N+1 integers where each integer is in the range [1, N] inclusive.

Example : Input : N= 5
                              Arr[5] = [3,1,3,4,2]
                  Output : 3

Duplicate in an array of N+1 integers in C
Algorithm :
Take the size of the array from the user and store it on variable say n.
Declare an array of size N and take N elements from the user.
Declare another array of size N+1 which holds the frequency of the elements present in the given array.
Now, iterate over the array and store the frequency of elements of the array in the another array .
Now, iterate over the declared array  and print those index which have value greater than 1.
Duplicate elements in an array in C
Code in C
Run
#include<stdio.h>

int main()
{

    int n;
    scanf("%d", &n);

    int arr[n];

    for(int i=0; i < n; i++)
        scanf("%d", &arr[i]);

    int temp[n+1];
    for(int i=0; i <= n; i++)
        temp[i]=0;

    for(int i=0; i < n; i++)
        temp[arr[i]]++;

    for(int i=1; i <= n; i++)
    {
        if(temp[i]>1)
            printf("%d ", i);
    }
    return 0;
}
Input
5
1 1 2 5 5
Output
1 5
Efficient Algorithm  to find duplicate in an array of N+1 integers in C :
Traverse the given array from 0 to n.
For every element in the array increment the (arr[i]-1)%n‘th element by n.
Now traverse the array again and print all those indices i for which (arr[i]-1)/n is greater than 2. Which guarantees that the number n has been added to that index.
Run
#include<stdio.h>

void printRepeating(int arr[], int n)
{
    for (int i = 0; i < n; i++)
    {
        int index = (arr[i]-1) % n;
        arr[index] += n;
    }

    for (int i = 0; i < n; i++)
    {
        if(((arr[i]-1) / n) >= 2)
            printf("%d ",i+1);
    }
}

// Driver code
int main()
{
    int n;
    scanf("%d", &n);

    int arr[n];
    for(int i=0; i < n; i++)
        scanf("%d", &arr[i]);

    printf("The repeating elements are: \n");

    // Function call
    printRepeating(arr, n);
    return 0;
}
