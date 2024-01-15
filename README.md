# Find-Players-With-Zero-or-One-Losses
You are given an integer array matches where matches[i] = [winneri, loseri] indicates that the player winneri defeated player loseri in a match.  Return a list answer of size 2 where:  answer[0] is a list of all players that have not lost any matches. answer[1] is a list of all players that have lost exactly one match.

class Solution:
    def findWinners(self, matches):
        losses = [0] * 100001

        for winner, loser in matches:
            if losses[winner] == 0:
                losses[winner] = -1

            if losses[loser] == -1:
                losses[loser] = 1
            else:
                losses[loser] += 1

        zero_loss = [i for i in range(1, 100001) if losses[i] == -1]
        one_loss = [i for i in range(1, 100001) if losses[i] == 1]

        return [zero_loss, one_loss]  
