# Ex-5 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.

STEP-2: Arrange the plain text in row columnar matrix format.

STEP-3: Now read the keyword depending on the number of columns of the plain text.

STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.

STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```
#include <stdio.h>
#include <string.h>

int main()
{
    char p[100], rail[20][100];
    int i, j, r, n, row = 0, dir = 1;

    printf("Enter Plain Text: ");
    scanf("%99s", p);

    printf("Enter Number of Rails: ");
    scanf("%d", &r);

    if(r < 2 || r > 20)
    {
        printf("Invalid number of rails");
        return 0;
    }

    n = strlen(p);

    for(i = 0; i < r; i++)
        for(j = 0; j < n; j++)
            rail[i][j] = '\0';

    for(i = 0; i < n; i++)
    {
        rail[row][i] = p[i];

        if(row == 0)
            dir = 1;
        else if(row == r - 1)
            dir = -1;

        row += dir;
    }

    printf("Encrypted Text: ");

    for(i = 0; i < r; i++)
        for(j = 0; j < n; j++)
            if(rail[i][j] != '\0')
                printf("%c", rail[i][j]);

    printf("\n");

    return 0;
}
```

# OUTPUT
<img width="287" height="120" alt="image" src="https://github.com/user-attachments/assets/25c146ba-3fe8-42df-83f9-42f9896c02b2" />


# RESULT

The Rail Fence Cipher encryption technique was implemented successfully.The program accepts the plaintext and number of rails from the user and displays the corresponding ciphertext.
