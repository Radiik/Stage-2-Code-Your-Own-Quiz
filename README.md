#text for easy, medium and hard difficulty
easy_text = '''Colour of sky is ___1___. Colour of blood is ___2___. \
Colour of trees is ___3___. Colour if sun is ___4___'''

medium_text = '''President of the United States is Barrack ___1___. \
His arch-rival is president of Russia Vladimir ___2___. It is likely that \
Barrack Obama is going to be replaced by Hilary ___3___ or Donald ___4___.'''

hard_text = '''Capitol of United Kingdom is ___1___. Capitol of France is \
___2___. Capitol of Italy is ___3___. Capitol of Spain is ___4___.'''

#list of blanks. It is used to find these elements inside text for difficulties
blanks_list = ["___1___", "___2___", "___3___", "___4___"]

#easy_answers, medium_answers, hard_answers
easy_answers = ["blue","red","green","yellow"]
medium_answers = ["Obama","Putin","Clinton","Trump"]
hard_answers = ["London","Paris","Rome","Madrid"]

#this is function for setting difficulty. However, inside is calling of function 
#game, so the overall game starts with set_difficulty
def set_difficulty():
	user_input = raw_input('''Please select a game difficulty by typing in! \
Possible choices include easy, medium, hard:''')
	if user_input == "easy":
		return game(easy_text, easy_answers)
	elif user_input == "medium":
		return game(medium_text, medium_answers)
	elif user_input == "hard":
		return game(hard_text, hard_answers)
#if user doesn't provide input easy, medium or hard, it will write please
#give proper input and asks again. 
	else:
		print"wrong answer, please select easy, medium or hard"
		set_difficulty()

#this is the main game function
def game(level,answers):
	#maximum numbers of bad attempts before game for one try, before game ower. 
	max_attempts = 4
	print level
	blanks = 0
	attempt = 1
#this creates wile loop for where it goes through four blanks inside a level text 
#and checks if the input is the same as answer from answers list(easy, hard or medium)
	while blanks < len(blanks_list):
		user_input = raw_input("please type an answer for" + blanks_list[blanks])
		if user_input == answers[blanks]:
			print "correct"
			level = level.replace(blanks_list[blanks],user_input)
			print level
			blanks += 1
#if the answer is incorrect, it prints down incorrect and writes number of
#remaining attempts
		else:
			if attempt == max_attempts:
				print "game over, you have reached maximum attempts for an answer"
				exit()
			attempt += 1	
			print "incorrect, you have" , ((max_attempts - attempt)+1), "remaining \
attempts"
	print "game completed succesfully"
	return
			

set_difficulty()
