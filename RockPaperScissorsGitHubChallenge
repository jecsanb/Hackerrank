import random

# returns what hand wins against
from collections import OrderedDict


def wins(hand):
    return {"R": "S", "P": "R", "S": "P"}.get(hand)


# returns what wins against hand
def beats(hand):
    return {"R": "P", "P": "S", "S": "R"}.get(hand)


# returns the winning hand of a Rock paper scissors match
def getwinner(handa, handb):
    if handa != handb:
        return handa if handb[1] == wins(handa[1]) else handb
    else:
        return None


# returns the number of time player a needs to change its hand to win against n -1 players which
# play the hands in formations.
def handformationchange(n, a, formations):
    if n == 1:
        return 0
    else:
        oddgame = (n % 2) != 0
        handchange = 0
        winners = OrderedDict()
        if oddgame:
            aw = formations.popitem()
            winners[aw[0]] = aw[1]
            n -= 1
        while len(formations):
            p1 = formations.popitem()
            p2 = formations.popitem()

            if p1[0] == a or p2[0] == a:
                poi = p1
                other = p2
                if a == p2[0]:
                    poi = p2
                    other = p1
                oldval = poi[1]
                newval = beats(other[1])
                if oddgame != newval and oldval is not None:
                    handchange += 1
                winners.update({poi[0]: newval})
                continue

            winner = getwinner(p1, p2)

            if winner is not None:
                if winner == p1:
                    winners.update({p1[0]: p1[1]})
                else:
                    winners.update({p2[0]: p2[1]})
        return handchange + handformationchange(len(winners), a, winners)


def getrandhand():
    r = random.randint(0, 2)
    return "RPS"[r]


def main():
    formations = ['S', 'R', None, 'R', 'S', 'R', 'R']
    n = len(formations)
    a = 2
    formationsd = OrderedDict()
    for key, val in enumerate(formations):
        formationsd.update({key: val})

    print(handformationchange(n, a, formationsd))


if __name__ == '__main__':
    main()
