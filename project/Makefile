NAME = minitalk
CLIENT = client
SERVER = server
SRCS_SERVER = src/server.c
SRCS_CLIENT = src/client.c
OBJS_SERVER = $(SRCS_SERVER:src/%.c=src/obj/%.o)
OBJS_CLIENT = $(SRCS_CLIENT:src/%.c=src/obj/%.o)
LIBFT = lib/libft/libft.a
CC = gcc
CFLAGS = -Wall -Werror -Wextra
RM = rm -f

$(NAME): $(SERVER) $(CLIENT)

$(SERVER): $(OBJS_SERVER)
	$(CC) $(CFLAGS) $(OBJS_SERVER) $(LIBFT) -o $(SERVER)

$(CLIENT): $(OBJS_CLIENT)
	$(CC) $(CFLAGS) $(OBJS_CLIENT) $(LIBFT) -o $(CLIENT)

src/obj/%.o: src/%.c | src/obj
	$(CC) $(CFLAGS) -c $< -o $@

src/obj:
	mkdir -p src/obj

clean:
	$(RM) $(OBJS_CLIENT) $(OBJS_SERVER)
	$(RM) -r src/obj

fclean: clean
	$(RM) $(CLIENT) $(SERVER)

re: fclean all

.PHONY: all clean fclean re
