# get_next_line

Bu proje, bir metin dosyasından satır satır okuma işlevini gerçekleştiren 'get_next_line' fonksiyonunu içermektedir.

## Proje Amacı

Bu proje, büyük metin dosyalarının verimli bir şekilde okunmasını sağlamak ve her seferinde tek bir satırın işlenmesini mümkün kılmak için geliştirilmiştir.

## Temel İşlevler

`get_next_line` fonksiyonu, verilen bir dosya tanımlayıcısından bir sonraki satırı okur ve döndürür. Dosyanın sonuna gelindiğinde veya bir hata oluştuğunda uygun değerler döndürür.

## Kullanım Örneği

```c
#include "get_next_line.h"
#include <stdio.h>
#include <fcntl.h>
#include <stdlib.h>

int main() {
    int fd = open("myfile.txt", O_RDONLY);

    char *line;
    while (get_next_line(fd, &line) > 0)
    {
        printf("%s\n", line);
        free(line);
    }

    if (get_next_line(fd, &line) == -1)
    {
        perror("get_next_line");
        free(line);
        close(fd);
        return (1);
    }
    free(line);
    close(fd);
    return (0);
}
