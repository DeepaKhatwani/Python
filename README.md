# Python

#Stores the amount in te variable
money =[1000,2000,3000,5000,10000,20000,40000,80000,160000,320000,640000,1250000,2500000,5000000,10000000]

slab = [10000, 320000]


p = open("database.txt", 'r')
lines = p.readlines()

question = []
first_option = []
second_option = []
third_option = []
fourth_option = []

#List for keeping record of all answer in sequence wise
ans_key=["D","B","A","C","B","A","B","B","C","B","D","D","A","A","C","C"]

cnt = len(lines)
cnt = 16
counter = 0

for i in range(cnt):    
    question.append(lines[counter])
    first_option.append(lines[counter + 1])
    second_option.append(lines[counter + 2])
    third_option.append(lines[counter + 3])
    fourth_option.append(lines[counter + 4])
    #ans_key.append(lines[counter + 5])
    #print(question[i])
    #print(first_option[i])
    #print(second_option[i])
    #print(third_option[i])
    #print(fourth_option[i])
    #print(ans_key[i])
    counter += 6

#print(p.readlines())
p.close()
#time.sleep(10)



inCorrect = False
stage = 0
Total_Earned_Money = 0


while(inCorrect == False):
   if(stage < len(money)):
       print(question[stage])
       print(first_option[stage])
       print(second_option[stage])
       print(third_option[stage])
       print(fourth_option[stage])
       print(ans_key[stage])
       x = input("Select your option: ")
       
       if(x.upper() == "50:50"):
           #Remove 2 wrong options
            print(question[stage])
            if(str(ans_key[stage]) == "A"):
                print(first_option[stage])
                print(second_option[stage])
            elif(str(ans_key[stage]) == "B"):
                print(first_option[stage])
                print(second_option[stage])
            elif(str(ans_key[stage]) == "C"):
                print(third_option[stage])
                print(fourth_option[stage])
            elif(str(ans_key[stage]) == "D"):
                print(third_option[stage])
                print(fourth_option[stage])
            print(ans_key[stage])
            x = input("Select your option: ")

       if(x.upper() != "QUIT"):
           if(str(x.upper()) == str(ans_key[stage].upper())):
               #--- Correct Answer ------
               Total_Earned_Money = money[stage]
               print("Correct answer")
               print("Money Earned: " + str(Total_Earned_Money))
               if (stage == 14):
                   print("Game finished")
               stage += 1
           else:
               #--- Incorrect Answer -----
               inCorrect = True              

               #--- Checking with Slab
               if(Total_Earned_Money < slab[1]):
                   if(Total_Earned_Money < slab[0]):
                       Total_Earned_Money = 0
                   elif(Total_Earned_Money >= slab[0]):
                       Total_Earned_Money = slab[0]
               elif(Total_Earned_Money >= slab[1]):
                   Total_Earned_Money = slab[1]

               print("Incorrect answer")        
               print("Money Won: " + str(Total_Earned_Money))          
       else:
           print("Money Won: " + str(Total_Earned_Money))
           print("Game finished")
           break;    
