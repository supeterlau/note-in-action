## install 安装

    # brew tap daviderestivo/emacs-head

    # brew install emacs-head --HEAD --with-cocoa --with-imagemagick --with-jansson

    # ln -s /usr/local/opt/emacs-head/Emacs.app /Applications

**Just Work**

brew tap d12frosted/emacs-plus

brew install emacs-plus@27 --HEAD --with-cocoa --with-imagemagick --with-jansson --with-no-frame-refocus --with-mailutils --with-dbus --with-modern-black-variant-icon --with-xwidgets 

--with-no-titlebar

To link the application to default Homebrew App location:
  ln -s /usr/local/opt/emacs-plus@27/Emacs.app /Applications

To have launchd start d12frosted/emacs-plus/emacs-plus@27 now and restart at login:
  brew services start d12frosted/emacs-plus/emacs-plus@27
Or, if you don't want/need a background service you can just run:
  emacs

重装第一步: 

  brew unlink emacs-plus@27

https://github.crookster.org/emacs27-from-homebrew-on-macos-with-emoji/

## base

### Keybind

https://ccrma.stanford.edu/guides/package/emacs/emacs.html

C-h 帮助
C-h k
C-h f
C-h l keys history

- move cursor

C-M-f ( forward-sexp )
C-M-b ( backward-sexp ) skip over one set of balanced parentheses, so you can see which parentheses match

M - < Start of Document
M - > End of Document

C-l middle of screen

M-g g (line-number)
  Starting with Emacs 23.2, ‘M-g g’ is bound to goto-line.

C-e end of line
M-e forward sentence
C-M-e end of defun

- file buffer

C-x C-f
C-x b switch buffers 新建，切换 buffer
C-x C-b 显示 buffer 列表
C-x k buffer <RET>
  Kill buffer buffer (kill-buffer).
M-x kill-some-buffers
  Offer to kill each buffer, one by one.
M-x kill-matching-buffers

C-x C- -> / C-x -> next-buffer switch to next buffer
C-x C- <- / C-x <- previous-buffer switch to previous buffer

C-x C-w 另存为
C-x C-v 关闭当前缓冲区，打开新文件
C-x i 光标处插入文件

C-x 2 切分成上下两个窗口
C-x 3 切分成左右两个窗口
C-x 1 关闭其他窗口
C-x 0 关闭当前窗口

C-x o 切换窗口

C-x C-2

https://www.emacswiki.org/emacs/AutoIndentation EmacsWiki: Auto Indentation
  C-j 总是执行 newline-and-indent
  
- search replace

C-s pattern

C-r pattern : search backwards

M-% oldstring <CR> newstring <CR>

替换：M-S-5

- copy paste

M-w copy
C-k cut line 剪切光标到行尾
C-y paste
C-w cut region
C-spc set mark ( C-@ ) 与输入法切换冲突
C-d 删除下一个字符

- edit

C-t 交换字符
M-t 交换单词
C-M-t 交换 s-expression

M-; comment/uncomment

Detele to beginning of line
  https://www.emacswiki.org/emacs/BackwardKillLine# EmacsWiki: Backward Kill Line

C-x C-e: Alt+x eval-last-sexp
Alt+x eval-region.
  http://ergoemacs.org/emacs/elisp_eval_lisp_code.html# Emacs: Evaluate Elisp Code

### Basic 

- start emacsclient

  启动 emacsclient 自动启动 emacsserver
    https://stackoverflow.com/questions/5570451/how-to-start-emacs-server-only-if-it-is-not-started configuration - How to start emacs server only if it is not started? - Stack Overflow
    https://news.ycombinator.com/item?id=9395056 Run `emacs -nw --daemon` to start a background emacs server. Now, you can do `e... | Hacker News
    https://unix.stackexchange.com/questions/74520/can-i-redirect-output-to-a-log-file-and-background-a-process-at-the-same-time bash - Can I redirect output to a log file and background a process at the same time? - Unix & Linux Stack Exchange
    https://emacs.stackexchange.com/questions/48717/launch-an-emacsclient-instance-in-a-new-terminal-window frames - Launch an emacsclient instance in a new terminal window - Emacs Stack Exchange

  emacsclient -t --create-frame --alternate-editor="vim" 

  ALTERNATE_EDITOR="" emacsclient -c

  emacsclient -cnq -a "" &@ &>> $HOME/.emacs.d/log/$(date +%Y-%m-%d).log &

  emacsclient -c 2>>$HOME/.emacs.d/log/error-$(date +'%Y-%m-%d').log &

  emacsclient -cnqu -a "" &@ 2>> $HOME/.emacs.d/log/$(date +%Y-%m-%d).log >> $HOME/.emacs.d/log/$(date +%Y-%m-%d).log & 

  (emacsclient -cqu -a "" &@ &>> $HOME/.emacs.d/log/$(date +%Y-%m-%d).log & )

  https://www.emacswiki.org/emacs/EmacsClient EmacsWiki: Emacs Client

  -V, --version		Just print version info and return
  -H, --help    		Print this usage information message
  -nw, -t, --tty 		Open a new Emacs frame on the current terminal
  -c, --create-frame    	Create a new frame instead of trying to
        use the current Emacs frame
  -s SOCKET, --socket-name=SOCKET
        Set filename of the UNIX socket for communication
  -f SERVER, --server-file=SERVER
        Set filename of the TCP authentication file
  -F ALIST, --frame-parameters=ALIST
        Set the parameters of a new frame
  -a EDITOR, --alternate-editor=EDITOR

  GUI applescript 运行

  https://emacs.stackexchange.com/questions/141/emacsdaemon-and-emacsclient-on-mac daemon - Emacsdaemon and Emacsclient on Mac - Emacs Stack Exchange

  https://stackoverflow.com/questions/25044592/use-gui-emacs-on-os-x-when-opening-files-with-emacsclient macos - Use GUI Emacs on OS X when opening files with emacsclient - Stack Overflow

- key rebind

https://stackoverflow.com/questions/3227039/rebind-c-space-in-emacs keyboard shortcuts - Rebind C-space in Emacs - Stack Overflow

(global-unset-key (kbd "C-SPC"))
(global-set-key (kbd "M-SPC") 'set-mark-command)

https://www.masteringemacs.org/article/mastering-key-bindings-emacs Mastering Key Bindings in Emacs - Mastering Emacs

- format code

elisp
  https://www.emacswiki.org/emacs/ElispFormat EmacsWiki: Elisp Format

- reload config

https://stackoverflow.com/questions/2580650/how-can-i-reload-emacs-after-changing-it How can I reload .emacs after changing it? - Stack Overflowhttps://stackoverflow.com/questions/2580650/how-can-i-reload-emacs-after-changing-it How can I reload .emacs after changing it? - Stack Overflow (may work for emacs, not emacs --daemon)

  M-x load-file
  M - > C-x C-e

- restore emacs state

https://www.gnu.org/software/emacs/manual/html_node/emacs/Saving-Emacs-Sessions.html Saving Emacs Sessions - GNU Emacs Manual

(desktop-save-mode 1)

desktop-path

https://stackoverflow.com/questions/4477376/some-emacs-desktop-save-questions-how-to-change-it-to-save-in-emacs-d-emacs/4485083#4485083 Some emacs desktop-save questions: how to change it to save in ~/.emacs.d/.emacs.desktop - Stack Overflow

- rename opend file

https://stackoverflow.com/questions/384284/how-do-i-rename-an-open-file-in-emacs/384612#384612

https://www.gnu.org/software/emacs/manual/html_node/emacs/Copying-and-Naming.html Copying and Naming - GNU Emacs Manual

- show line number

(when (version<= "26.0.50" emacs-version )
  (global-display-line-numbers-mode))

(column-number-mode 1)

- comment block

selection commands built into Emacs

word	mark-word	M-@
paragraph	mark-paragraph	M-h
page	mark-page	C-x C-p
buffer	mark-whole-buffer 	C-x h
function	mark-defun	C-M-h
balanced expression	mark-sexp	C-M-@

https://www.johndcook.com/blog/2017/08/09/selecting-things-in-emacs/# Selecting things in Emacs

https://stackoverflow.com/questions/5612092/is-there-a-way-to-comment-out-a-large-chunk-of-code# emacs - Is there a way to comment out a large chunk of code? - Stack Overflow
 M-;

- geometry

http://kimi.im/2019-02-09-emacs-frame-dimention 设置 Emacs 窗口大小

- copy and paste

https://www.emacswiki.org/emacs/CopyAndPaste EmacsWiki: Copy And Paste

- auto save

https://www.gnu.org/software/emacs/manual/html_node/emacs/Auto-Save-Files.html#Auto-Save-Files Auto Save Files - GNU Emacs Manual

- load config

https://emacs.stackexchange.com/questions/33332/recursively-list-all-files-and-sub-directories Recursively list all files and sub-directories - Emacs Stack Exchange

https://www.emacswiki.org/emacs/LoadPath EmacsWiki: Load Path

(add-to-list 'load-path "~/.emacs.d/lisp/")

https://www.gnu.org/software/emacs/manual/html_node/eintr/Loading-Files.html Loading Files - Programming in Emacs Lisp

;;; Emacs Load Path
(setq load-path (cons "~/emacs" load-path))

- run code in Emacs

https://www.masteringemacs.org/article/compiling-running-scripts-emacs Compiling and running scripts in Emacs - Mastering Emacs

### config

https://www.john2x.com/emacs.html John's Emacs Config

入口 init.el

配置 config/
  basic.el
  packages.el

包列表 packages.el

init.el

镜像 elpa
(setq package-archives '(("gnu"   . "http://elpa.emacs-china.org/gnu/")
                        ("melpa" . "http://elpa.emacs-china.org/melpa/")))

(desktop-save-mode 1)
(global-auto-revert-mode 1)

### erlang

https://erlang.org/doc/apps/tools/erlang_mode_chapter.html#setup-on-unix

https://github.com/massemanet/distel massemanet/distel: emacs - erlang IDE

macOS use asdf:

  ~/.asdf/installs/erlang/23.0.2/lib/tools-3.4/emacs/

  (setq load-path (cons  "~/.asdf/installs/erlang/23.0.2/lib/tools-3.4/emacs"
      load-path))
      (setq erlang-root-dir "~/.asdf/installs/erlang/23.0.2/")
      (setq exec-path (cons "~/.asdf/installs/erlang/23.0.2/bin" exec-path))
      (require 'erlang-start)

https://medium.com/swlh/installing-and-configuring-emacs-development-on-linux-378414a06bbc

https://www.lambdacat.com/post-modern-emacs-setup-for-erlang/

https://gist.github.com/jaseemabid/75f5607304a8186ba228

https://github.com/massemanet/distel

### mail

https://rakhim.org/fastmail-setup-with-emacs-mu4e-and-mbsync-on-macos/ Fastmail setup with Emacs, mu4e and mbsync on macOS - Rakhim.org

## advanced

## IDE ???

http://worace.works/2016/06/07/getting-started-with-emacs-for-ruby/ Getting Started with Emacs for Ruby · Horace Williams

## Packages

- use-package

https://jwiegley.github.io/use-package/keywords/ Keywords — use-package

- magit

https://magit.vc/manual/magit/Getting-Started.html#Getting-Started Getting Started (Magit User Manual)

## Online

https://www.gnu.org/software/emacs/tour/index.html

https://www.gnu.org/software/emacs/manual/html_node/emacs/index.html

https://www.gnu.org/software/emacs/further-information.html

https://www.gnu.org/software/emacs/

http://git.savannah.gnu.org/cgit/emacs.git

https://emacs-china.org/

https://www.fsf.org/

http://emacsrocks.com/

https://planet.emacslife.com/ Planet Emacslife

## Tool

https://jwiegley.github.io/use-package/installation/ Installation — use-package

https://github.com/myrjola/diminish.el myrjola/diminish.el: Diminished modes are minor modes with no modeline display

https://elpa.gnu.org/packages/delight.html GNU ELPA - delight

https://github.com/tkf/emacs-request tkf/emacs-request: Request.el -- Easy HTTP request for Emacs Lisp

https://github.com/emacs-china/elpa emacs-china/elpa: Emacs China ELPA 镜像

https://github.com/BlueFlo0d/xwwp/tree/xwwp-ace-dev BlueFlo0d/xwwp at xwwp-ace-dev (Browser in Emacs)

https://github.com/cask/cask cask/cask: Project management tool for Emacs

## Ref

### 配置参考
    https://www.john2x.com/emacs.html#org94dcd83 John's Emacs Config

    https://github.com/victorolinasc/dot_emacs victorolinasc/dot_emacs: My Emacs portable configuration
      https://medium.com/swlh/installing-and-configuring-emacs-development-on-linux-378414a06bbc Installing and configuring Emacs development on Linux | by Victor Nascimento | The Startup | Medium
      https://medium.com/@victor.nascimento/elixir-development-on-emacs-9f6776265e4d Elixir development on Emacs. After configuring the basic stuff on… | by Victor Nascimento | Medium

    http://ergoemacs.org/emacs/emacs_make_modern.html Emacs: Init File Tutorial

    https://www.gtrun.org/custom/init.html My Doom Emacs config

    https://emacs.nasy.moe/ Emacs Configuration

    https://github.com/purcell/emacs.d purcell/emacs.d: An Emacs configuration bundle with batteries included

    http://aaronbedra.com/emacs.d/
    https://github.com/magnars/.emacs.d
    https://github.com/technomancy/better-defaults technomancy/better-defaults: A small number of better defaults for Emacs
    https://github.com/seagle0128/.emacs.d seagle0128/.emacs.d: Centaur Emacs - A Fancy and Fast Emacs Configuration

    https://pages.sachachua.com/.emacs.d/Sacha.html Sacha Chua's Emacs configuration

    https://github.com/DiegoVicen/my-emacs DiegoVicen/my-emacs: My Emacs configuration

https://github.com/daviderestivo/homebrew-emacs-head
https://github.com/d12frosted/homebrew-emacs-plus

Learn:
  http://ergoemacs.org/emacs/emacs.html Practical Emacs Tutorial

  https://finiteheap.com/emacs/2020/04/26/my-emacs-journey.html My Emacs Journey | Finite Heap

https://blog.aaronbieber.com/2016/12/29/don-t-use-terminal-emacs.html Don't Use Terminal Emacs - The Chronicle

https://www.chrislockard.net/posts/2020-05-15-compiling-emacs-27-macos/

https://dev.to/brandelune/building-emacs-from-source-on-macos-5cck
https://www.cs.cornell.edu/courses/cs3110/2009sp/software/install-emacs.html
https://www.aidanscannell.com/post/setting-up-an-emacs-playground-on-mac/
https://finiteheap.com/emacs/2020/04/26/my-emacs-journey.html
https://github.crookster.org/emacs27-from-homebrew-on-macos-with-emoji/

https://sachachua.com/blog/2019/04/2019-04-29-emacs-news/

https://lispcookbook.github.io/cl-cookbook/windows.html
https://portacle.github.io/ Portacle is a complete IDE for Common Lisp that you can take with you on a USB stick
https://lispcookbook.github.io/cl-cookbook/ The Common Lisp Cookbook
https://lispcookbook.github.io/cl-cookbook/emacs-ide.html


Data Structures and Functional Programming https://www.cs.cornell.edu/courses/cs3110/2020sp/

https://sourcethemes.com/academic/