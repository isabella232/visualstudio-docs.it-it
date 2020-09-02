---
title: Identificatori di formato nel debugger (C++) | Microsoft Docs
ms.date: 3/11/2019
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- C++
helpviewer_keywords:
- QuickWatch dialog box, format specifiers in C++
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- expressions [C++], format specifiers
- specifiers, watch variable format
- specifiers
- Watch window, format specifiers in C++
- watch variable symbols
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 0f6f3b7c-ce2c-4b4d-b14f-7589dbed5444
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 8e6be79bc38e9283493bf5b7428a21c17cf9d3e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62896620"
---
# <a name="format-specifiers-for-c-in-the-visual-studio-debugger"></a>Identificatori di formato per C++ nel debugger di Visual Studio
È possibile modificare il formato in cui un valore viene visualizzato nelle finestre **espressioni di controllo**, **auto**e **variabili locali** utilizzando identificatori di formato.

È anche possibile usare gli identificatori di formato nella finestra di **controllo immediato** , nella finestra di **comando** , in [punti](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)e persino nelle finestre di origine. Se si sospende un'espressione in queste finestre, il risultato verrà visualizzato in un [DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). La visualizzazione Suggerimento dati riflette l'identificatore di formato.

> [!NOTE]
> Quando il debugger nativo di Visual Studio è stato modificato in un nuovo motore di debug, sono stati aggiunti alcuni nuovi identificatori di formato e alcuni precedenti sono stati rimossi. Il debugger precedente viene ancora usato per il debug di interoperabilità (nativo e gestito combinati) con C++/CLI.

## <a name="set-format-specifiers"></a>Imposta identificatori di formato
Verrà usato il codice di esempio seguente:

```C++
int main() {
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

Aggiungere la `my_var1` variabile alla finestra **espressioni di controllo** durante il debug, **eseguire il debug**di  >  **Windows**  >  **Watch**  >  **Watch 1**. Fare quindi clic con il pulsante destro del mouse sulla variabile e scegliere **visualizzazione esadecimale**. A questo punto la finestra **espressioni di controllo** Mostra il valore 0x0065. Per visualizzare questo valore espresso come carattere anziché come Integer, fare prima clic con il pulsante destro del mouse e deselezionare la **visualizzazione esadecimale**. Aggiungere quindi l'identificatore di formato carattere **, c** nella colonna **nome** dopo il nome della variabile. La colonna **valore** ora Mostra **101 "e"**.

![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")

::: moniker range=">= vs-2019" 
È possibile visualizzare e selezionare da un elenco di identificatori di formato disponibili aggiungendo una virgola (,) al valore nella finestra **espressioni di controllo** . 

![WatchFormatSpecDropdown](../debugger/media/vs-2019/format-specs-cpp.png "FormatSpecCpp")

::: moniker-end

## <a name="format-specifiers"></a><a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Identificatori di formato
Nelle tabelle seguenti vengono descritti gli identificatori di formato che è possibile utilizzare in Visual Studio. Gli identificatori in grassetto sono supportati solo per il nuovo debugger e non per il debug di interoperabilità con C++/CLI.

::: moniker range=">= vs-2019" 

|Identificatore|Formato|Valore dell'espressione di controllo originale|Valore visualizzato|
|---------------|------------|--------------------------|---------------------|
|d|intero decimale|0x00000066|102|
|o|intero ottale senza segno|0x00000066|000000000146|
|x<br /><br /> **h**|intero esadecimale|102|0xcccccccc|
|X<br /><br /> **H**|intero esadecimale|102|0xcccccccc|
|xb<br /><br /> **HB**|intero esadecimale (senza 0x iniziale)|102|cccccccc|
|Xb<br /><br /> **Hb**|intero esadecimale (senza 0x iniziale)|102|CCCCCCCC|
|b|intero binario senza segno|25|0b00000000000000000000000000011001|
|bb|intero binario senza segno (senza 0b iniziale)|25|00000000000000000000000000011001|
|e|notazione scientifica|25000000|2.500000 e + 07|
|g|abbreviazione della notazione scientifica o del formato a virgola mobile|25000000|2.5 e + 07|
|c|Carattere singolo|0x0065, c|101 'e'|
|s|stringa const char * (con virgolette)|\<location> "Hello World"|"hello world"|
|**SB**|Stringa const char* (senza virgolette)|\<location> "Hello World"|hello world|
|s8|stringa UTF-8|\<location> "Si tratta di una tazza di caffè UTF-8 â ̃ •"|"Si tratta di una ☕ di Coffee Cup UTF-8"|
|**s8b**|Stringa UTF-8 (senza virgolette)|\<location> "Hello World"|hello world|
|su|Stringa Unicode (codifica UTF-16) (con virgolette)|\<location> L "Hello World"|L"hello world"<br /><br /> u"hello world"|
|sub|Stringa Unicode (codifica UTF-16) (senza virgolette)|\<location> L "Hello World"|hello world|
|bstr|Stringa binaria BSTR (con virgolette)|\<location> L "Hello World"|L"hello world"|
|env|Blocco di ambiente (stringa con terminazione Null doppia)|\<location>L "=:: =:: \\ \\ "|L"=::=::\\\\\\0=C:=C:\\\\windows\\\\system32\\0ALLUSERSPROFILE=...|
|**s32**|Stringa UTF-32 (con virgolette)|\<location> U "Hello World"|u"hello world"|
|**s32b**|stringa UTF-32 (senza virgolette)|\<location> U "Hello World"|hello world|
|**en**|enum|Saturday(6)|Sabato|
|**hv**|Tipo di puntatore: indica che il valore del puntatore in esame è il risultato dell'allocazione di heap di una matrice, ad esempio `new int[3]`.|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, ...}|
|**na**|Elimina l'indirizzo di memoria di un puntatore a un oggetto.|\<location>, {member = Value...}|{member=value…}|
|**ND**|Visualizza solo le informazioni sulla classe base, ignorando le classi derivate|`(Shape*) square` include informazioni sulla classe base e sulle classi derivate|Visualizza solo informazioni sulla classe base|
|h|HRESULT o codice di errore Win32. Questo identificatore non è più necessario per gli HRESULT perché il debugger li decodifica automaticamente.|S_OK|S_OK|
|wc|flag della classe di finestre|0x0010|WC_DEFAULTCHAR|
|wm|Numeri di messaggio Windows|16|WM_CLOSE|
|nr|Elimina la voce "Visualizzazione non elaborata"|
|nvo|Mostra l'elemento "visualizzazione non elaborata" solo per i valori numerici|
|!|formato non elaborato in cui vengono ignorate le personalizzazioni delle visualizzazioni del tipo di dati|\<customized representation>|4|

::: moniker-end

::: moniker range="vs-2017" 

|Identificatore|Formato|Valore dell'espressione di controllo originale|Valore visualizzato|
|---------------|------------|--------------------------|---------------------|
|d|intero decimale|0x00000066|102|
|o|intero ottale senza segno|0x00000066|000000000146|
|x<br /><br /> **h**|intero esadecimale|102|0xcccccccc|
|X<br /><br /> **H**|intero esadecimale|102|0xcccccccc|
|c|Carattere singolo|0x0065, c|101 'e'|
|s|stringa const char * (con virgolette)|\<location> "Hello World"|"hello world"|
|**SB**|Stringa const char* (senza virgolette)|\<location> "Hello World"|hello world|
|s8|stringa UTF-8|\<location> "Si tratta di una tazza di caffè UTF-8 â ̃ •"|"Si tratta di una ☕ di Coffee Cup UTF-8"|
|**s8b**|Stringa UTF-8 (senza virgolette)|\<location> "Hello World"|hello world|
|su|Stringa Unicode (codifica UTF-16) (con virgolette)|\<location> L "Hello World"|L"hello world"<br /><br /> u"hello world"|
|sub|Stringa Unicode (codifica UTF-16) (senza virgolette)|\<location> L "Hello World"|hello world|
|bstr|Stringa binaria BSTR (con virgolette)|\<location> L "Hello World"|L"hello world"|
|env|Blocco di ambiente (stringa con terminazione Null doppia)|\<location>L "=:: =:: \\ \\ "|L"=::=::\\\\\\0=C:=C:\\\\windows\\\\system32\\0ALLUSERSPROFILE=...|
|**s32**|Stringa UTF-32 (con virgolette)|\<location> U "Hello World"|u"hello world"|
|**s32b**|stringa UTF-32 (senza virgolette)|\<location> U "Hello World"|hello world|
|**en**|enum|Saturday(6)|Sabato|
|**hv**|Tipo di puntatore: indica che il valore del puntatore in esame è il risultato dell'allocazione di heap di una matrice, ad esempio `new int[3]`.|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, ...}|
|**na**|Elimina l'indirizzo di memoria di un puntatore a un oggetto.|\<location>, {member = Value...}|{member=value…}|
|**ND**|Visualizza solo le informazioni sulla classe base, ignorando le classi derivate|`(Shape*) square` include informazioni sulla classe base e sulle classi derivate|Visualizza solo informazioni sulla classe base|
|h|HRESULT o codice di errore Win32. Questo identificatore non è più necessario per gli HRESULT perché il debugger li decodifica automaticamente.|S_OK|S_OK|
|wc|flag della classe di finestre|0x0010|WC_DEFAULTCHAR|
|wm|Numeri di messaggio Windows|16|WM_CLOSE|
|!|formato non elaborato in cui vengono ignorate le personalizzazioni delle visualizzazioni del tipo di dati|\<customized representation>|4|

::: moniker-end

> [!NOTE]
> Quando è presente l'identificatore di formato **HV** , il debugger tenta di determinare la lunghezza del buffer e visualizza tale numero di elementi. Poiché il debugger non sempre riesce a individuare le dimensioni esatte del buffer di una matrice, è consigliabile usare un identificatore della dimensione `(pBuffer,[bufferSize])` , se possibile. L'identificatore di formato **HV** è utile quando la dimensione del buffer non è immediatamente disponibile.

### <a name="size-specifiers-for-pointers-as-arrays"></a><a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Identificatori di dimensioni per puntatori quali matrici
Se è presente un puntatore a un oggetto che si vuole visualizzare come matrice, è possibile usare un numero intero o un'espressione per specificare il numero di elementi di matrice.

|Identificatore|Formato|Valore dell'espressione di controllo originale|Valore visualizzato|
|---------------|------------|---------------------------|---------------------|
|n|Intero decimale o **esadecimale**|pBuffer,[32]<br /><br /> pBuffer,**[0x20]**|Visualizza `pBuffer` come matrice di 32 elementi.|
|**exp**|Espressione C++ valida che restituisce un numero intero.|pBuffer,[bufferSize]|Visualizza pBuffer come matrice di elementi `bufferSize` .|
|**expand(n)**|Espressione C++ valida che restituisce un numero intero|pBuffer, expand(2)|Visualizza il terzo elemento di  `pBuffer`|

## <a name="format-specifiers-for-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Identificatori di formato per il debug di interoperabilità con C++/CLI
Gli identificatori in **grassetto** sono supportati solo per il debug di codice nativo e C++/CLI.

|Identificatore|Formato|Valore dell'espressione di controllo originale|Valore visualizzato|
|---------------|------------|--------------------------|---------------------|
|**d**<br /><br />**i**|Intero con segno decimale|0xF000F065|-268373915|
|**u**|Intero senza segno decimale|0x0065|101|
|o|intero ottale senza segno|0xF065|0170145|
|x<br /><br />X|intero esadecimale|61541|0x0000f065|
|**l**<br /><br />**h**|prefisso lungo o breve per: d, i, u, o, x, X|00406042|0x0c22|
|**f**|virgola mobile signed|(3./2.), f|1.500000|
|**e**|notazione scientifica signed|(3.0/2.0)|1.500000e+000|
|**g**|virgola mobile signed o notazione scientifica firmata,<br/> qualunque sia il più breve|(3.0/2.0)|1.5|
|c|Carattere singolo|\<location>|101 'e'|
|s|const char * (con virgolette)|\<location>|"hello world"|
|su|const wchar_t*<br /><br /> const char16_t \* (con virgolette)|\<location>|L"hello world"|
|sub|const wchar_t*<br /><br /> const char16_t\*|\<location>|hello world|
|s8|const char * (con virgolette)|\<location>|"hello world"|
|h|HRESULT o codice di errore Win32.<br/>Questo identificatore non è più necessario per gli HRESULT perché il debugger li decodifica automaticamente.|S_OK|S_OK|
|wc|flag della classe di finestre|0x00000040,|WC_DEFAULTCHAR|
|wm|Numeri di messaggio Windows|0x0010|WM_CLOSE|
|!|formato non elaborato, ignorando le personalizzazioni delle visualizzazioni del tipo di dati|\<customized representation>|4|

### <a name="format-specifiers-for-memory-locations-in-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Identificatori di formato per i percorsi di memoria nel debug di interoperabilità con C++/CLI
Nella tabella seguente vengono descritti i simboli di formattazione utilizzati per le posizioni di memoria. Gli identificatori della posizione di memoria possono essere usati con qualsiasi valore o espressione che restituisce una posizione.

|Simbolo|Formato|Valore dell'espressione di controllo originale|Valore visualizzato|
|------------|------------|--------------------------|---------------------|
|**ma**|64 caratteri ASCII|0x0012ffac|0x0012ffac .4...0...".0W&.......1W&.0.:W..1...."..1.JO&.1.2.."..1...0y....1|
|**m**|16 byte in formato esadecimale, seguiti da 16 caratteri ASCII|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|
|**MB**|16 byte in formato esadecimale, seguiti da 16 caratteri ASCII|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|
|**MW**|8 parole|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|
|**md**|4 parole doppie|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|
|**mq**|2 parole quadruple|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|
|**MU**|caratteri da 2 byte (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|

### <a name="size-specifier-for-pointers-as-arrays-in-interop-debugging-with-ccli"></a><a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> Identificatore di dimensioni per puntatori quali matrici nel debug di interoperabilità con C++/CLI
Se è presente un puntatore a un oggetto che si vuole visualizzare come matrice, è possibile usare un numero intero per specificare il numero di elementi di matrice.

|Identificatore|Formato|Expression|Valore visualizzato|
|---------------|------------|----------------|---------------------|
|n|intero decimale|pBuffer[32]|Visualizza `pBuffer` come matrice di 32 elementi.|