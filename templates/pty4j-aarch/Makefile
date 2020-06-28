#*******************************************************************************
# Copyright (c) 2002, 2009 QNX Software Systems and others.
# All rights reserved. This program and the accompanying materials
# are made available under the terms of the Eclipse Public License v1.0
# which accompanies this distribution, and is available at
# http://www.eclipse.org/legal/epl-v10.html
#
# Contributors:
#     QNX Software Systems - initial API and implementation
#     Alex Blewitt - MacOSX with a 64-bit vm
#*******************************************************************************/

# Defaults which can be overridden.
LINUX=linux
AARCH = {{ ansible_architecture }}

CC=gcc
LD=libtool
CPPFLAGS = -I.
CFLAGS +=-B/usr/lib/aarch-linux-gnu -fpic -D_REENTRANT -D_GNU_SOURCE

ARCH_FLAG_AARCH =

INSTALL_DIR_LINUX_AARCH = ../os/$(LINUX)/$(AARCH)

LIB_NAME_PTY = libpty.so

LIB_NAME_FULL_PTY_LINUX_AARCH = $(INSTALL_DIR_LINUX_AARCH)/libpty.so

OBJS_PTY_AARCH = exec_pty_$(AARCH).o openpty_$(AARCH).o pfind_$(AARCH).o

OBJS_AARCH = $(OBJS_PTY_AARCH)

all: linux_{{ ansible_architecture }}

linux_{{ ansible_architecture }}: $(LIB_NAME_FULL_PTY_LINUX_AARCH)

rebuild: clean all

$(LIB_NAME_FULL_PTY_LINUX_AARCH): $(OBJS_PTY_AARCH)
		mkdir -p $(INSTALL_DIR_LINUX_AARCH)
		$(CC) -g -shared -Wl,-soname,$(LIB_NAME_PTY) $(LDFLAGS) -o $(LIB_NAME_FULL_PTY_LINUX_AARCH) $(OBJS_PTY_AARCH)

exec_pty_$(AARCH).o: exec_pty.c
		$(CC) $(CFLAGS) $(ARCH_FLAG_AARCH) $(CPPFLAGS) -c -o $@ exec_pty.c

openpty_$(AARCH).o: openpty.c
		$(CC) $(CFLAGS) $(ARCH_FLAG_AARCH) $(CPPFLAGS) -c -o $@ openpty.c

pfind_$(AARCH).o: pfind.c
		$(CC) $(CFLAGS) $(ARCH_FLAG_AARCH) $(CPPFLAGS) -c -o $@ pfind.c

clean :
		$(RM) $(OBJS_AARCH) $(LIB_NAME_FULL_PTY_LINUX_AARCH)
