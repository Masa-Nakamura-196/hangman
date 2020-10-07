# ハングマンゲーム　2020.8.22

def hangman(word):
    wrong = 0
    stages = ["",
              "_____________          ",
              "|           |          ",
              "|           |          ",
              "|           |          ",
              "|           |          ",
              "|           0          ",
              "|          _|_         ",
              "|           |          ",
              "|          _|_         ",
              "|                      ",
              "|                      ",
              ]
    rletters = list(word)
    board = ["_"] * len(word)
    win = False
    print("ハングマンへようこそ！")

    while wrong < len(stages) - 1:
        print("\n")                   # 空行
        print("\n")
        print("\n")
        msg = "一文字を予想してね:"
        char = input(msg)
        if char in rletters:
            cind = rletters.index(char)    #indexは初めの方のもじのindex
            board[cind] = char
            rletters[cind] = '$'      #文字が複数該当したときにうまく作動するように
        else:                         #indexは最初に該当した要素のindexしか返さない
            wrong += 1
        print(" ".join(board))
        e = wrong + 1
        print("\n".join(stages[0:e]))   #stageリストの間を改行することで、うまく図示
        if "_" not in board:
            print("あなたの勝ち！")
            print(" ".join(board))
            win = True
            break
    if not win:
        print("\n".join(stages[0:wrong+1]))
        print("あなたの負け！正解は {} .".format(word))


WORD_list_1A = ["provide", "merchant", "needle", "fasten", "mental", "object", "produce", "progress", "finished", "oxygen", "observactory"]

import random                                                            # 引数の単語をランダム化する

Secret_number_random = random.randint(0,10)                              # 単語追加したときに、index変えるのを忘れずに！！！

DX_Question_word_10 = WORD_list_1A[Secret_number_random]

hangman(DX_Question_word_10)
