NAME = philo
OBJDIR = obj
CC = cc
RM = rm -f
CFLAGS = -Wall -Wextra -Werror -fsanitize=thread

SRC 		= fork.c\
			ft_strtol.c\
			init.c\
			main.c\
			routine.c\
			start.c\
			time.c\
			utils.c

OBJ = $(SRC:%.c=$(OBJDIR)/%.o)

all: $(NAME)

$(NAME): $(LIBFT) $(OBJ)
	$(CC) $(CFLAGS) $(OBJ) -o $(NAME) -lpthread

$(OBJDIR)/%.o: %.c
	@mkdir -p $(dir $@)
	$(CC) $(CFLAGS) -c $< -o $@

clean:
	$(RM) -r $(OBJDIR)

fclean: clean
	$(RM) $(NAME)

re: fclean all

.PHONY:		all clean fclean re
