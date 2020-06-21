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
AARCH_64 = aarch64

CC=gcc
LD=libtool
CPPFLAGS = -I.
CFLAGS +=-B/usr/lib/aarch-linux-gnu -fpic -D_REENTRANT -D_GNU_SOURCE

ARCH_FLAG_AARCH_64 =

INSTALL_DIR_LINUX_AARCH_64 = ../os/$(LINUX)/$(AARCH_64)

LIB_NAME_PTY = libpty.so

LIB_NAME_FULL_PTY_LINUX_AARCH_64 = $(INSTALL_DIR_LINUX_AARCH_64)/libpty.so

OBJS_PTY_X86_64 = exec_pty_$(AARCH_64).o openpty_$(AARCH_64).o pfind_$(AARCH_64).o

OBJS_AARCH_64 = $(OBJS_PTY_X86_64)

all: linux_aarch64

linux_aarch64: $(LIB_NAME_FULL_PTY_LINUX_AARCH_64)

rebuild: clean all

$(LIB_NAME_FULL_PTY_LINUX_AARCH_64): $(OBJS_PTY_X86_64)
		mkdir -p $(INSTALL_DIR_LINUX_AARCH_64)
		$(CC) -g -shared -Wl,-soname,$(LIB_NAME_PTY) $(LDFLAGS) -o $(LIB_NAME_FULL_PTY_LINUX_AARCH_64) $(OBJS_PTY_X86_64)

exec_pty_$(AARCH_64).o: exec_pty.c
		$(CC) $(CFLAGS) $(ARCH_FLAG_AARCH_64) $(CPPFLAGS) -c -o $@ exec_pty.c

openpty_$(AARCH_64).o: openpty.c
		$(CC) $(CFLAGS) $(ARCH_FLAG_AARCH_64) $(CPPFLAGS) -c -o $@ openpty.c

pfind_$(AARCH_64).o: pfind.c
		$(CC) $(CFLAGS) $(ARCH_FLAG_AARCH_64) $(CPPFLAGS) -c -o $@ pfind.c

clean :
		$(RM) $(OBJS_AARCH_64) $(LIB_NAME_FULL_PTY_LINUX_AARCH_64)
