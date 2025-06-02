CC = cc
CFLAGS = -O3 -Wall -Wextra -Werror -g -pthread
NAME = philo

LIBFT = libs/libft
LIBX = libs/minilibx-linux

SRCS = src/main.c \
			src/utils/colors.c \
			src/utils/dev/printers.C \
			src/parser/parser.c src/parser/utils.c \
			src/philo/philo.c \

GREEN = \033[32m
RED = \033[31m
DEF_COLOR = \033[0m
TERM_UP = \033[A

OBJS = $(SRCS:.c=.o)

all: $(NAME)
	@(echo "$(TERM_UP)$(GREEN)Compilation Successful!$(DEF_COLOR)")

$(NAME): $(OBJS)
	@$(MAKE) -C $(LIBFT) -s all ||\
		(echo "$(TERM_UP)$(RED)Error in libft compilation!$(DEF_COLOR)" && exit 1)
	@$(MAKE) -C $(LIBX) -s all ||\
		(echo "$(TERM_UP)$(RED)Error in MLX compilation!$(DEF_COLOR)" && exit 1)
	@$(CC) $(CFLAGS) $(OBJS) -L $(LIBFT) -lft -L $(LIBX) -lmlx -o $(NAME) || \
		(echo "$(TERM_UP)$(RED)Error during linking!$(DEF_COLOR)" && exit 1)

%.o: %.c
	@$(CC) $(CFLAGS) -c $< -o $@ ||\
		(echo "$(TERM_UP)$(RED)Error compiling $< !\ncannot generate $@$(DEF_COLOR)" && exit 1)

clean:
	@rm -f $(OBJS)
	@echo "$(TERM_UP)$(GREEN)Clean Successful!$(DEF_COLOR)"

fclean: clean
	@$(MAKE) -C $(LIBFT) -s fclean ||\
		(echo "$(TERM_UP)$(RED)Error in libft cleaning!$(DEF_COLOR)" && exit 1)
	@rm -f $(NAME)
	@echo "$(TERM_UP)$(GREEN)Full clean Successful!$(DEF_COLOR)"

re: fclean all

.PHONY: all clean fclean re
