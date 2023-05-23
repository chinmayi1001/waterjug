from collections import defaultdict
jug1,jug2,aim=7,8,2
#initialize default dictionary with lambda value as false
visited=defaultdict(lambda:False)
def WaterJugSolver(amt1,amt2):
  #check for goal state and check whether goal is reached then return true
  if (amt1==aim and amt2 ==0) or (amt2==aim and amt1==0):
    print(amt1,amt2)
    return True
  #check if already visited
  if visited[(amt1,amt2)]==False:
    print(amt1,amt2)
    visited[(amt1,amt2)]=True
    return WaterJugSolver(0,amt2)or WaterJugSolver(amt1,0) or WaterJugSolver(jug1,amt2) or WaterJugSolver(amt1,jug2) or WaterJugSolver(amt1 + min(amt2, (jug1-amt1)),
                amt2 - min(amt2, (jug1-amt1))) or WaterJugSolver(amt1 - min(amt1, (jug2-amt2)),
                amt2 + min(amt1, (jug2-amt2)))

  else:
    return False
  print("Steps:")  

WaterJugSolver(0,0)