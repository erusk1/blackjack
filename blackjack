import random
class card:
  def __init__(card, suit, value, face):
    card.suit = suit
    card.value = value
    card.face = face
#card organization notes; 
# numbered c1-c52
#first in a suit is ace
# final 3 in a suit are face cards
#c1-c13 clubs
#c14-c26 spades
#c27-c39 diamonds
#c40-c52 hearts

c1=card('club',1,'ace')
c2=card('club',2,None)
c3=card('club',3,None)
c4=card('club',4,None)
c5=card('club',5,None)
c6=card('club',6,None)
c7=card('club',7,None)
c8=card('club',8,None)
c9=card('club',9,None)
c10=card('club',10,None)
c11=card('club',10,'jack')
c12=card('club',10,'queen')
c13=card('club',10,'king')
c14=card('spade',1,'ace')
c15=card('spade',2,None)
c16=card('spade',3,None)
c17=card('spade',4,None)
c18=card('spade',5,None)
c19=card('spade',6,None)
c20=card('spade',7,None)
c21=card('spade',8,None)
c22=card('spade',9,None)
c23=card('spade',10,None)
c24=card('spade',10,'jack')
c25=card('spade',10,'queen')
c26=card('spade',10,'king')
c27=card('diamond',1,'ace')
c28=card('diamond',2,None)
c29=card('diamond',3,None)
c30=card('diamond',4,None)
c31=card('diamond',5,None)
c32=card('diamond',6,None)
c33=card('diamond',7,None)
c34=card('diamond',8,None)
c35=card('diamond',9,None)
c36=card('diamond',10,None)
c37=card('diamond',10,'jack')
c38=card('diamond',10,'queen')
c39=card('diamond',10,'king')
c40=card('heart',1,'ace')
c41=card('heart',2,None)
c42=card('heart',3,None)
c43=card('heart',4,None)
c44=card('heart',5,None)
c45=card('heart',6,None)
c46=card('heart',7,None)
c47=card('heart',8,None)
c48=card('heart',9,None)
c49=card('heart',10,None)
c50=card('heart',10,'jack')
c51=card('heart',10,'queen')
c52=card('heart',10,'king')

deck = [c1,c2,c3,c4,c5,c6,c7,c8,c9,c10,c11,c12,c13,c14,c15,c16,c17,c18,c19,c20,c21,c22,c23,c24,c25,c26,c27,c28,c29,c30,c31,c32,c33,c34,c35,c36,c37,c38,c39,c40,c41,c42,c43,c44,c45,c46,c47,c48,c49,c50,c51,c52]

def draw(deck):
  top = deck[random.randrange(0,len(deck))-1]
  deck.remove(top)
  return top

def printhand(player_hand):
    print("your hand:")
    for x in player_hand:
      if x.face ==None:
        print( str(x.value) + " of " + x.suit + "s")
      else:
        print( x.face + " of " + x.suit + "s")
def printdealerhand(dealer_hand):
    x = dealer_hand[0]
    print("dealer's hand:")
    if x.face ==None:
      print( str(x.value) + " of " + x.suit + "s")
    else:
      print( x.face + " of " + x.suit + "s")


def hand_sum(hand):
  for x in hand:
    if x.face == 'ace':
      hand.remove(x)
      hand_value = [1,11]
      for x in hand:
        hand_value[0] += x.value
        hand_value[1] += x.value
      return tuple(hand_value)
  else:
    hand_value = 0
    for x in hand:
      hand_value += x.value
    return hand_value

def hit(hand): #had to create 2 hit and print hand functions, couldn't figure out how to make a if player or dealer's test
  current_hand = hand_sum(hand)
  take = draw(deck)
  hand.append(take) 
  print("you draw.")
  printhand(hand)
  if take.face == 'ace':
    if type(current_hand) == tuple:
      return(current_hand[0] + 1, current_hand[0] + 11, current_hand[1] + 1, current_hand[1] + 11)
    else:
      return(current_hand + 1, current_hand + 11)
  else:
    if type(current_hand) ==tuple:
      return(current_hand[0] + take.value, current_hand[1] + take.value)
    else:
      return(current_hand + take.value)
  
def dealerhit(hand):
  current_hand = hand_sum(hand)
  take = draw(deck)
  hand.append(take) 
  print("dealer draws.")
  if take.face == 'ace':
    if type(current_hand) == 'list':
      return (current_hand[0] + 1, current_hand[0] + 11, current_hand[1] + 1, current_hand[1] + 11)
    else:
      return (current_hand + 1, current_hand + 11)
  else:
    if type(current_hand) =='list':
      return (current_hand[0] + take.value, current_hand[1] + take.value)
    else:
      return (current_hand + take.value)

def revealhand(dealer_hand):
  print("dealer's hand:")
  for x in dealer_hand:
    if x.face ==None:
      print( str(x.value) + " of " + x.suit + "s")
    else:
      print( x.face + " of " + x.suit + "s")
    

def act(hand_value, player_hand, dealer_hand):
  player_turn = True
  while blackjack(hand_value) < 21:
    inp=int(input("1. hit 2. stand"))
    if inp ==1: 
      hand_value = hit(player_hand) #prints new hand and returns new player hand value
      print(str(hand_value))
      if blackjack(hand_value) > 21:
        print("Bust. You lose.")
        if input("play again?\n") :
          break
    elif inp ==2:
      return hand_value
      break#ends 'hit()' loop so player can proceed
  else:
    main()

def blackjack(hand_value): #blackjack() must return an int, otherwise our win if's cannot cover every condition. blackjack() is to convert tuple hand_value's to their correspond int
  if type(hand_value) == tuple:
    for x in hand_value:
      if x == 21:
        return 21
      elif hand_value[0] > 21:
        return hand_value[0]
      elif hand_value[1] < 21:
        return hand_value[1]
      else:
        return hand_value[0]
  else:
    if hand_value == 21:
      return 21
    else:
      return hand_value

def house(dealer_hand):
  house_sum = hand_sum(dealer_hand)
  if type(house_sum) == 'tuple':
    for x in house_sum:
      while x <= 15: 
        house_sum = dealerhit(dealer_hand) # i hope this returns house_sum tuple that has a minm > 15if house_sum
  else:
    while blackjack(house_sum) <= 15: # 2 while loops, this one for int (other for tupl)
      house_sum = dealerhit(dealer_hand)
      revealhand(dealer_hand)
      print(house_sum)
    else:
      revealhand(dealer_hand)
      print(house_sum)
      return house_sum


def game(player_hand_value, player_hand, dealer_hand): #initially had this for final hand value eval; corrected to account for initial hand value eval.
  player_hand_final_value = blackjack(act(player_hand_value, player_hand, dealer_hand))
  dealer_hand_final_value = blackjack(house(dealer_hand))
  if player_hand_final_value == 21:
    if dealer_hand_final_value == 21:
      print("tie.")
      if input("play again?\n") :
        main()
    else:
      print("you win.")
      if input("play again?\n") :
        main()
  elif player_hand_final_value < 21:
    if dealer_hand_final_value > 21:
      print("Dealer bust. You win.")
      if input("play again?\n") :
        main()
    elif dealer_hand_final_value == 21:
      print("you lose.")
      if input("play again?\n") :
        main()
    elif dealer_hand_final_value > player_hand_final_value:
      print("you lose.")
      if input("play again?\n") :
        main()
    elif dealer_hand_final_value < player_hand_final_value:
      print("you win.")
      if input("play again?\n") :
        main()
  
def beforegame(player_hand,dealer_hand):
  begin_hand = blackjack(hand_sum(player_hand))
  begin_dealerhand = blackjack(hand_sum(dealer_hand))
  if begin_dealerhand == 21 and begin_hand == 21:
    printdealerhand(dealer_hand)
    print("tie.")
    if input("play again?\n") :
      main()
  elif begin_dealerhand ==21:
    printdealerhand(dealer_hand)
    print("You lose.")
    if input("play again?\n") :
      main()
  elif begin_hand ==21:
    printdealerhand(dealer_hand)
    print("You win.")
    if input("Play again?\n") :
      main()
 

def main():
  start = int(input("1. deal\n"))
  if start :
    while True :
      player_hand = [draw(deck),draw(deck)]
      dealer_hand = [draw(deck),draw(deck)]
      player_hand_value = hand_sum(player_hand)
      printhand(player_hand)
      print(player_hand_value)
      printdealerhand(dealer_hand)
      beforegame(player_hand, dealer_hand)
      game(player_hand_value, player_hand, dealer_hand)
  
main()
