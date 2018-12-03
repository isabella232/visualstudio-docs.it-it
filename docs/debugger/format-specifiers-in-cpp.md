---
title: Formattare gli identificatori nel debugger (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/20/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- CSharp
- VB
- FSharp
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
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 73cd5655a5cb843c29fb628a2ec233860410dc7c
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305741"
---
# <a name="format-specifiers-for-c-in-the-visual-studio-debugger"></a>Identificatori di formato per C++ nel debugger di Visual Studio
È possibile modificare il formato in cui viene visualizzato il valore nella **Watch** finestra usando identificatori di formato.  
  
 È anche possibile usare gli identificatori di formato nel **controllo immediato** finestra, il **comando** finestra, in [i punti di analisi](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)e persino nelle finestre di origine. Se posiziona su un'espressione in queste finestre, il risultato viene visualizzato una [suggerimento dati](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). La visualizzazione Suggerimento dati riflette l'identificatore di formato.  
  
> [!NOTE]
>  Quando il debugger nativo di Visual Studio è cambiato in un nuovo motore di debug, sono stati aggiunti nuovi identificatori di formato e alcuni precedenti sono state rimosse. Il debugger precedente viene ancora usato per il debug di interoperabilità (nativo e gestito combinati) con C++/CLI. 
  
## <a name="set-format-specifiers"></a>Set di identificatori di formato  
Si userà l'esempio di codice seguente:  
  
```C++  
int main() {  
    int my_var1 = 0x0065;  
    int my_var2 = 0x0066;  
    int my_var3 = 0x0067;  
}  
```  
  
 Aggiungere la `my_var1` variabile per il **Watch** finestra durante il debug **Debug** > **Windows** > **guarda**  >  **Espressione di controllo 1**. Successivamente, la variabile e scegliere **visualizzazione esadecimale**. A questo punto il **Watch** finestra Mostra il valore 0x0065. Per visualizzare questo valore espresso come un carattere anziché a un numero intero, prima di tutto fare doppio clic e deselezionare **visualizzazione esadecimale**. Quindi aggiungere l'identificatore di formato di carattere **, c** nel **nome** colonna dopo il nome della variabile. Il **valore** colonna Visualizza ora **101 'e'**.  
  
 ![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")  
  
##  <a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Identificatori di formato  
 Nelle tabelle seguenti vengono descritti gli identificatori di formato che è possibile usare in Visual Studio. Gli identificatori in grassetto sono supportati solo per il nuovo debugger e non per il debug di interoperabilità con C + + / CLI.  
  
|Identificatore|Formato|Valore dell'espressione di controllo originale|Valore visualizzato|  
|---------------|------------|--------------------------|---------------------|  
|d|intero decimale|0x00000066|102|  
|o|intero ottale senza segno|0x00000066|000000000146|  
|x<br /><br /> **h**|intero esadecimale|102|0xcccccccc|  
|x<br /><br /> **H**|intero esadecimale|102|0xcccccccc|  
|c|carattere singolo|0x0065, c|101 'e'|  
|s|stringa const char * (tra virgolette)|\<posizione > "hello world"|"hello world"|  
|**sb**|Stringa const char* (senza virgolette)|\<posizione > "hello world"|hello world|  
|s8|stringa UTF-8|\<posizione > "This is â˜• una tazza di caffè UTF-8"|"This is ☕ una tazza di caffè UTF-8"|
|**s8b**|Stringa UTF-8 (senza virgolette)|\<posizione > "hello world"|hello world|  
|su|Stringa Unicode (codifica UTF-16) (con le virgolette)|\<posizione > L "hello world"|L"hello world"<br /><br /> u"hello world"|  
|sub|Stringa Unicode (codifica UTF-16) (senza virgolette)|\<posizione > L "hello world"|hello world|  
|bstr|Stringa binaria di BSTR (tra virgolette)|\<posizione > L "hello world"|L"hello world"|  
|env|Blocco di ambiente (stringa con terminazione Null doppia)|\<posizione > L "=:: =::/\\\\"|L "=:: =::/\\\\\\0 = C: = C:\\\\windows\\\\system32\\0ALLUSERSPROFILE =...|
|**s32**|Stringa UTF-32 (tra virgolette)|\<posizione > U "hello world"|u"hello world"|  
|**s32b**|stringa UTF-32 (senza virgolette)|\<posizione > U "hello world"|hello world|  
|**en**|enum|Saturday(6)|Saturday|  
|**hv**|Tipo di puntatore: indica che il valore del puntatore in esame è il risultato dell'allocazione di heap di una matrice, ad esempio `new int[3]`.|\<posizione>{\<primo membro>}|\<posizione > {\<primo membro >, \<secondo membro >,...}|  
|**na**|Elimina l'indirizzo di memoria di un puntatore a un oggetto.|\<posizione>, {member=value…}|{member=value…}|  
|**nd**|Visualizza solo le informazioni sulla classe base, ignorando le classi derivate|`(Shape*) square` include informazioni sulla classe base e sulle classi derivate|Visualizza solo informazioni sulla classe base|  
|hr|HRESULT o codice di errore Win32. Questo identificatore non è più necessario per valori HRESULT come il debugger decodifica li automaticamente.|S_OK|S_OK|  
|wc|flag della classe di finestre|0x0010|WC_DEFAULTCHAR|  
|wm|Numeri di messaggio Windows|16|WM_CLOSE|  
|!|formato non elaborato in cui vengono ignorate le personalizzazioni delle visualizzazioni del tipo di dati|\<rappresentazione personalizzata>|4|  
  
> [!NOTE]
>  Quando la **hv** identificatore di formato è presente, il debugger tenta di determinare la lunghezza del buffer e visualizza il numero di elementi. Poiché il debugger non sempre riesce a individuare le dimensioni esatte del buffer di una matrice, è consigliabile usare un identificatore della dimensione `(pBuffer,[bufferSize])` , se possibile. Il **hv** identificatore di formato è utile quando le dimensioni del buffer non sono prontamente disponibile  
  
###  <a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Identificatori di dimensioni per puntatori quali matrici  
 Se è presente un puntatore a un oggetto che si vuole visualizzare come matrice, è possibile usare un numero intero o un'espressione per specificare il numero di elementi di matrice. 
  
|Identificatore|Formato|Valore dell'espressione di controllo originale|Valore visualizzato|  
|---------------|------------|---------------------------|---------------------|  
|n|Intero decimale o **esadecimale**|pBuffer,[32]<br /><br /> pBuffer,**[0x20]**|Visualizza `pBuffer` come matrice di 32 elementi.|  
|**[exp]**|Espressione C++ valida che restituisce un numero intero.|pBuffer,[bufferSize]|Visualizza pBuffer come matrice di elementi `bufferSize` .|  
|**expand(n)**|Espressione C++ valida che restituisce un numero intero|pBuffer, expand(2)|Visualizza il terzo elemento di  `pBuffer`|  
  
##  <a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Identificatori di formato per il debug di interoperabilità con C++/CLI  
 Gli identificatori in **grassetto** sono supportati solo per il debug di codice nativo e C++/CLI.  
  
|Identificatore|Formato|Valore dell'espressione di controllo originale|Valore visualizzato|  
|---------------|------------|--------------------------|---------------------|  
|**d**<br /><br />**i**|Intero con segno decimale|0xF000F065|-268373915|  
|**u**|Intero senza segno decimale|0x0065|101|  
|o|intero ottale senza segno|0xF065|0170145|  
|x<br /><br />x|intero esadecimale|61541|0x0000f065|  
|**l**<br /><br />**h**|prefisso lungo o breve per: d, i, u, o, x, X|00406042|0x0c22|  
|**f**|virgola mobile signed|(3./2.), f|1.500000|  
|**e**|notazione scientifica signed|(3.0/2.0)|1.500000e+000|  
|**g**|accesso automatico a virgola mobile signed o notazione scientifica,<br/> qualunque sia il più breve|(3.0/2.0)|1,5|  
|c|carattere singolo|\<posizione>|101 'e'|  
|s|const char * (tra virgolette)|\<posizione>|"hello world"|  
|su|const wchar_t*<br /><br /> char16_t const\* (tra virgolette)|\<posizione>|L"hello world"|  
|sub|const wchar_t*<br /><br /> const char16_t\*|\<posizione>|hello world|  
|s8|const char * (tra virgolette)|\<posizione>|"hello world"|  
|hr|HRESULT o codice di errore Win32.<br/>Questo identificatore non è più necessario per valori HRESULT come il debugger decodifica li automaticamente.|S_OK|S_OK|  
|wc|flag della classe di finestre|0x00000040,|WC_DEFAULTCHAR|  
|wm|Numeri di messaggio Windows|0x0010|WM_CLOSE|  
|!|formato non elaborato, ignorando eventuali personalizzazioni di visualizzazione tipo di dati|\<rappresentazione personalizzata>|4|  
  
###  <a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Per le posizioni di memoria nel debug di interoperabilità con identificatori di formato c++ /CLI  
 La tabella seguente descrive i simboli di formattazione utilizzati per le posizioni di memoria. Gli identificatori della posizione di memoria possono essere usati con qualsiasi valore o espressione che restituisce una posizione.  
  
|Simbolo|Formato|Valore dell'espressione di controllo originale|Valore visualizzato|  
|------------|------------|--------------------------|---------------------|  
|**ma**|64 caratteri ASCII|0x0012ffac|0x0012ffac .4...0...".0W&.......1W&.0.:W..1...."..1.JO&.1.2.."..1...0y....1|  
|**m**|16 byte in formato esadecimale, seguiti da 16 caratteri ASCII|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|  
|**mb**|16 byte in formato esadecimale, seguiti da 16 caratteri ASCII|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|  
|**mw**|8 parole|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|  
|**md**|4 parole doppie|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|  
|**mq**|2 parole quadruple|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|  
|**mu**|caratteri da 2 byte (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|  
  
###  <a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> Identificatore di dimensioni per puntatori quali matrici nel debug di interoperabilità con C++/CLI  
 Se è presente un puntatore a un oggetto che si vuole visualizzare come matrice, è possibile usare un numero intero per specificare il numero di elementi di matrice.
  
|Identificatore|Formato|Espressione|Valore visualizzato|  
|---------------|------------|----------------|---------------------|  
|n|intero decimale|pBuffer[32]|Visualizza `pBuffer` come matrice di 32 elementi.|
