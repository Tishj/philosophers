# **************************************************************************** #
#                                                                              #
#                                                         ::::::::             #
#    Makefile                                           :+:    :+:             #
#                                                      +:+                     #
#    By: tbruinem <tbruinem@student.codam.nl>         +#+                      #
#                                                    +#+                       #
#    Created: 2020/07/15 15:30:15 by tbruinem      #+#    #+#                  #
#    Updated: 2020/11/04 14:44:54 by tbruinem      ########   odam.nl          #
#                                                                              #
# **************************************************************************** #

NAME =		philo_one
SRC_DIR =	src
OBJ_DIR =	obj
TAIL =		-pthread
INCL =		-I incl/
FLAGS =		-Wall -Wextra -Werror
SRC	=		main.c \
			philosopher.c \
			data.c \
			threads.c \
			mutex_handling.c \
			utils.c \
			message.c \
			status_check.c

OBJ := $(addprefix $(OBJ_DIR)/, $(SRC:%.c=%.o))
SRC := $(addprefix $(SRC_DIR)/, $(SRC))

ifeq ($(DEBUG),1)
FLAGS += -g -fsanitize=address
endif

#Only viable on linux, on mac this is broken
ifeq ($(DEBUG),2)
FLAGS += -g -fsanitize=thread
endif

all: $(NAME)

obj/%.o: src/%.c
	@mkdir -p $(@D)
	@echo "Compiling $@"
	@$(CC) -c $(FLAGS) $(INCL) $< $(TAIL) -o $@

$(NAME): $(OBJ)
	@$(CC) $(FLAGS) $(INCL) $(TAIL) $^ -o $@
	@echo "Succesfully compiled $(NAME)"

clean:
	@rm -rf $(OBJ)
	@echo "Done cleaning"

fclean: clean
	@rm -rf $(NAME)
	@echo "Done fcleaning"

re: fclean all
