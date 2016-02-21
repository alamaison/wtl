# Copyright 2016 Alexander Lamaison. All rights reserved.
#
# This file is a part of the Windows Template Library.
# The use and distribution terms for this software are covered by the
# Common Public License 1.0 (http://opensource.org/licenses/cpl.php)
# which can be found in the file CPL.TXT at the root of this distribution.
# By using this software in any fashion, you are agreeing to be bound by
# the terms of this license. You must not remove this notice, or
# any other, from this software.

add_executable(MemDlg WIN32 stdafx.cpp MemDlg.cpp MemDlg.rc)
target_link_libraries(MemDlg PRIVATE WTL)
set_target_properties(MemDlg PROPERTIES LINK_FLAGS " /MANIFEST:NO")
