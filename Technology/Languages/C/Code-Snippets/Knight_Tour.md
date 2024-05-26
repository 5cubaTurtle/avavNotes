
requirements:
-recursive.
-bitset.
-array of locations of the knight each move.
- 5 min timeout.
|
|
    |
    |
          |
    |
   |
||----|----|----------|----|---|
|
|
    |-17
|
          |-15
|
   |
          |
    |-6
|
|
|
    |
    |kight here
|
    |
   |
|
|6
   |
    |
          |
    |10
 |
|
|
    |15
  |
          |17
  |
   |

|UPLEFT
      |pos > 15
 |pos % 8 > 0
|-17
|
|------------|----------|------------|----|
|UPRIGHT
     |pos > 15 
|pos % 8 < 7
|-15
|
|LEFTUP
      |pos > 9
  |pos % 8 > 1
|-10
|
|RIGHTUP
     |pos > 7
  |pos % 8 < 6
|- 6
|
|LEFTDOWN
    |pos < 56
 |pos % 8 > 1
|6
   |
|RIGHTDOWN...
|pos < 54
 |pos % 8 < 6
|10
  |

position 18 takes 14 minutes to run. 

The code:
```c
#include <stdio.h>    /*printf*/
#include <time.h>    /*time*/
#include <assert.h>
#include <stdlib.h>    /*exit*/
enum jmp_direction { UPLEFT = -17, UPRIGHT = -15, LEFTUP = -10, RIGHTUP = -6,
                    LEFTDOWN = 6, RIGHTDOWN = 10, DOWNLEFT = 15, DOWNRIGHT = 17 };
int knightstour(int pos);
void print_board(unsigned long brd);
int go(int pos, unsigned long board, time_t start);
int main(int argc, char **argv, char **envp) {
    int i = 0;
    for(i = 19; i < 64; ++i)
		if(knightstour(i))
			printf("%dth position OK\n", i);

    return 0;
}

int knightstour(int pos) {
    unsigned long initial_position = 1;
    assert(pos >= 0 && pos < 64);
    time_t start = time(NULL);
    initial_position <<= pos;
    return go(pos, initial_position, start);
}

int go(int pos, unsigned long board, time_t start) {
    unsigned long cur_loc = 0;
    time_t now = time(NULL);
    cur_loc = 1UL << pos;
    /*printf("%lu\n", board);*/
    printf("current location:\n");
    print_board(cur_loc);
    printf("The board:\n");
    print_board(board);
    putchar('\n');
    if(now >= start + 300)    /*5 min timer*/
    {
        fprintf(stderr, "timeout\n");
        exit(EXIT_FAILURE);
    }
    if(!(~board))
    {
        printf("success\n");
        printf("The board:\n");
        print_board(board);
        return 1;
    }
        if(pos < 32 && pos % 8 < 4)
        {
            if(pos > 15 && pos % 8 > 0 && !(board & cur_loc >> 17))
                if(go(pos + UPLEFT, board | cur_loc >> 17, start))
                    return 1;

            if(pos > 9 && pos % 8 > 1 && !(board & cur_loc >> 10))
                if(go(pos + LEFTUP, board | cur_loc >> 10, start))
                    return 1;

            if(pos > 15 && pos % 8 < 7 && !(board & cur_loc >> 15))
                if(go(pos + UPRIGHT, board | cur_loc >> 15, start))
                    return 1;

            if(pos > 7 && pos % 8 < 6 && !(board & cur_loc >> 6))
                if(go(pos + RIGHTUP, board | cur_loc >> 6, start))
                    return 1;

            if(pos < 54 && pos % 8 < 6 && !(board & cur_loc << 10))
                if(go(pos + RIGHTDOWN, board | cur_loc << 10, start))
                    return 1;

            if(pos < 48 && pos % 8 < 7 && !(board & cur_loc << 17))
                if(go(pos + DOWNRIGHT, board | cur_loc << 17, start))
                    return 1;

            if(pos < 48 && pos % 8 > 0 && !(board & cur_loc << 15))
                if(go(pos + DOWNLEFT, board | cur_loc << 15, start))
                    return 1;

            if(pos < 56 && pos % 8 > 1 && !(board & cur_loc << 6))
                if(go(pos + LEFTDOWN, board | cur_loc << 6, start))
                    return 1;

            return 0;
		}
        else if(pos < 32 && pos % 8 > 3)
        {
            if(pos > 15 && pos % 8 < 7 && !(board & cur_loc >> 15))
                if(go(pos + UPRIGHT, board | cur_loc >> 15, start))
                    return 1;

            if(pos > 7 && pos % 8 < 6 && !(board & cur_loc >> 6))
                if(go(pos + RIGHTUP, board | cur_loc >> 6, start))
                    return 1;

            if(pos < 54 && pos % 8 < 6 && !(board & cur_loc << 10))
                if(go(pos + RIGHTDOWN, board | cur_loc << 10, start))
                    return 1;

            if(pos < 48 && pos % 8 < 7 && !(board & cur_loc << 17))
                if(go(pos + DOWNRIGHT, board | cur_loc << 17, start))
                    return 1;

            if(pos < 48 && pos % 8 > 0 && !(board & cur_loc << 15))
                if(go(pos + DOWNLEFT, board | cur_loc << 15, start))
                    return 1;

            if(pos < 56 && pos % 8 > 1 && !(board & cur_loc << 6))
                if(go(pos + LEFTDOWN, board | cur_loc << 6, start))
                    return 1;

            if(pos > 9 && pos % 8 > 1 && !(board & cur_loc >> 10))
                if(go(pos + LEFTUP, board | cur_loc >> 10, start))
                    return 1;

            if(pos > 15 && pos % 8 > 0 && !(board & cur_loc >> 17))
                if(go(pos + UPLEFT, board | cur_loc >> 17, start))
                    return 1;

            return 0;
        }

        else if(pos > 31 && pos % 8 > 3)
        {
            if(pos < 54 && pos % 8 < 6 && !(board & cur_loc << 10))
                if(go(pos + RIGHTDOWN, board | cur_loc << 10, start))
                    return 1;

            if(pos < 48 && pos % 8 < 7 && !(board & cur_loc << 17))
                if(go(pos + DOWNRIGHT, board | cur_loc << 17, start))
                    return 1;

            if(pos < 48 && pos % 8 > 0 && !(board & cur_loc << 15))
                if(go(pos + DOWNLEFT, board | cur_loc << 15, start))
                    return 1;

            if(pos < 56 && pos % 8 > 1 && !(board & cur_loc << 6))
                if(go(pos + LEFTDOWN, board | cur_loc << 6, start))
                    return 1;

            if(pos > 9 && pos % 8 > 1 && !(board & cur_loc >> 10))
                if(go(pos + LEFTUP, board | cur_loc >> 10, start))
                    return 1;

            if(pos > 15 && pos % 8 > 0 && !(board & cur_loc >> 17))
                if(go(pos + UPLEFT, board | cur_loc >> 17, start))
                    return 1;

            if(pos > 15 && pos % 8 < 7 && !(board & cur_loc >> 15))
                if(go(pos + UPRIGHT, board | cur_loc >> 15, start))
                    return 1;

            if(pos > 7 && pos % 8 < 6 && !(board & cur_loc >> 6))
                if(go(pos + RIGHTUP, board | cur_loc >> 6, start))
                    return 1;

            return 0;
        }
        else
        {
            if(pos < 48 && pos % 8 > 0 && !(board & cur_loc << 15))
                if(go(pos + DOWNLEFT, board | cur_loc << 15, start))
                    return 1;

            if(pos < 56 && pos % 8 > 1 && !(board & cur_loc << 6))
                if(go(pos + LEFTDOWN, board | cur_loc << 6, start))
                    return 1;

            if(pos > 9 && pos % 8 > 1 && !(board & cur_loc >> 10))
                if(go(pos + LEFTUP, board | cur_loc >> 10, start))
                    return 1;

            if(pos > 15 && pos % 8 > 0 && !(board & cur_loc >> 17))
                if(go(pos + UPLEFT, board | cur_loc >> 17, start))
                    return 1;

            if(pos > 15 && pos % 8 < 7 && !(board & cur_loc >> 15))
                if(go(pos + UPRIGHT, board | cur_loc >> 15, start))
                    return 1;

            if(pos > 7 && pos % 8 < 6 && !(board & cur_loc >> 6))
                if(go(pos + RIGHTUP, board | cur_loc >> 6, start))
                    return 1;

            if(pos < 54 && pos % 8 < 6 && !(board & cur_loc << 10))
                if(go(pos + RIGHTDOWN, board | cur_loc << 10, start))
                    return 1;

            if(pos < 48 && pos % 8 < 7 && !(board & cur_loc << 17))
                if(go(pos + DOWNRIGHT, board | cur_loc << 17, start))
                    return 1;
            return 0;
        }
}

void print_board(unsigned long brd)
{
    unsigned long mask = 1;
    int i = 0;
    for(i = 0; i < 64; mask <<= 1, ++i)
    {
        if(brd & mask)
        {
            putchar(' ');
            putchar('+');
        }

        else
        {
            putchar(' ');
            putchar('.');
        }

        if(mask & 0x8080808080808080UL)
        {
            putchar('\n');
        }
    }
}
```