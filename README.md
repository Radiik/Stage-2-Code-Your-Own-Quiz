level_easy = '''A ___1___ is created with the def keyword. You specify the inputs a ___1___ takes by adding ___2___ separated by commas between the parentheses. ___1___s by default return ___3___ if you don't specify the value to return. ___2___ can be standard data types such as string, number, dictionary, tuple, and ___4___ or can be more complicated such as objects and lambda functions.'''

level_medium = '''President of the United States is Barrack ___1___. His arch-rival is president of Russia Vladimir ___2___. It is likely that Barrack Obama is going to be replaced by Hilary ___3___ or Donald ___4___.'''

level_hard = '''Capitol of United Kingdom is ___1___. Capitol of France is ___2___. Capitol of Italy is ___3___. Capitol of Spain is ___4___.'''

numbers_list = ["___1___", "___2___", "___3___", "___4___"]


#easy_answers, medium_answers, hard_answers
easy_answers = ["function","parameters","None","list"]
medium_answers = ["Obama","Putin","Clinton","Trump"]
hard_answers = ["London","Paris","Rome","Madrid"]

# Checks if a word in parts_of_speech is a substring of the word passed in.
def word_in_pos(word, numbers_list):
    for pos in numbers_list:
        if pos in word:
            return pos
    return None


def my_fill(level_easy, level_medium, level_hard, easy_answers, medium_answers, hard_answers,numbers_list):
	level = raw_input("Please select a game difficulty by typing in! Possible choices include easy, medium, hard:")
	print "level selected: " + level
	replaced = []
	
	
	if level == "easy":
		print level_easy
		devided = level_easy.split()
		for word in devided:
			replacement = word_in_pos(word,numbers_list)
			if replacement != None:
				user_input = raw_input("type an answer for" + replacement)
				
				if user_input == easy_answers[0]:
					print "correct"
				else:
					print "fail"
					
				word = word.replace(replacement, user_input)
				replaced.append(word)
			else:
				replaced.append(word)
		replaced = " ".join(replaced)
    	return replaced
    	
	
	if level == "medium":
		print level_medium
	if level == "hard":
		print level_hard

print my_fill(level_easy, level_medium, level_hard, easy_answers, medium_answers, hard_answers, numbers_list)
