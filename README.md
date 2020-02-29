При установке Brick по инструкции с https://github.com/buglloc/brick вы можете столкнуться со следующей проблемой: 

2.0/gtk/gtkfilechooserbutton.h:60:8: error: unnecessary parentheses in declaration of ‘__gtk_reserved2’ [-Werror=parentheses] void (*__gtk_reserved2); ^ /usr/include/gtk-2.0/gtk/gtkfilechooserbutton.h:61:8: error: unnecessary parentheses in declaration of ‘__gtk_reserved3’ [-Werror=parentheses] void (*__gtk_reserved3); ^ /usr/include/gtk-2.0/gtk/gtkfilechooserbutton.h:62:8: error: unnecessary parentheses in declaration of ‘__gtk_reserved4’ [-Werror=parentheses] void (*__gtk_reserved4); ^ /usr/include/gtk-2.0/gtk/gtkfilechooserbutton.h:63:8: error: unnecessary parentheses in declaration of ‘__gtk_reserved5’ [-Werror=parentheses] void (*__gtk_reserved5); ^ /usr/include/gtk-2.0/gtk/gtkfilechooserbutton.h:64:8: error: unnecessary parentheses in declaration of ‘__gtk_reserved6’ [-Werror=parentheses] void (*__gtk_reserved6); ^ /usr/include/gtk-2.0/gtk/gtkfilechooserbutton.h:65:8: error: unnecessary parentheses in declaration of ‘__gtk_reserved7’ [-Werror=parentheses] void (*__gtk_reserved7); ^ In file included from /usr/include/gtk-2.0/gtk/gtk.h:173, from

Для её устранения необходимо в файле ~/tmp/brick/macros.cmake добавить в 153 строку значение: 

STRING(REGEX REPLACE "(^| )-I" " -isystem " FLL_CFLAGS "${FLL_CFLAGS}")

Или просто скачать файл macros.cmake отсюда: https://github.com/SokolovGIT/brickfixed/blob/master/macros.cmake и заменить его в ~/tmp/brick/macros.cmake

За помощь в решении проблемы отдельная благодарность пользователю @Artalus
