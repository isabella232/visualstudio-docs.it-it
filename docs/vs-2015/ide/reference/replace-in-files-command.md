---
title: Comando Sostituisci nei file | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8398f07cf6fa6bd2702b2d84ab0d29dcd614ed32
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157808"
---
# <a name="replace-in-files-command"></a>Comando Sostituisci nei file
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sostituisce il testo nei file usando un subset delle opzioni disponibili nella scheda **Sostituisci nei file** della finestra **Trova e sostituisci**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]  
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]  
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]  
```  
  
## <a name="arguments"></a>Argomenti  
 `findwhat`  
 Obbligatorio. Testo da cercare.  
  
 `replacewith`  
 Obbligatorio. Il testo di sostituzione per il testo corrispondente.  
  
## <a name="switches"></a>Opzioni  
 /all o /a  
 facoltativo. Sostituisce tutte le occorrenze del testo di ricerca con il testo di sostituzione.  
  
 /case o /c  
 facoltativo. Vengono rilevate corrispondenze solo se i caratteri maiuscoli e minuscoli corrispondono esattamente a quelli specificati nell'argomento `findwhat`.  
  
 /ext: `extensions`  
 facoltativo. Specifica l'estensione dei file nei quali eseguire la ricerca.  
  
 /keep o /k  
 facoltativo. Indica che tutti i file modificati vengono lasciati aperti.  
  
 /lookin: `searchpath`  
 facoltativo. Directory in cui eseguire la ricerca. Se il percorso contiene spazi, racchiudere l'intero percorso tra virgolette.  
  
 /options o /t  
 facoltativo. Visualizza l'elenco delle impostazioni correnti dell'opzione di ricerca e non esegue una ricerca.  
  
 /regex o /r  
 facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni che rappresentano modelli di testo anziché i caratteri letterali. Per l'elenco completo dei caratteri espressione regolare, vedere [Espressioni regolari](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 /reset o /e  
 facoltativo. Ripristina le impostazioni predefinite delle opzioni di ricerca e non esegue la ricerca.  
  
 /stop  
 facoltativo. Se è in corso un'operazione di ricerca, la interrompe. Quando viene specificato `/stop` la sostituzione ignora tutti gli altri argomenti. Ad esempio, per interrompere la sostituzione corrente immettere quanto segue:  
  
```  
>Edit.ReplaceinFiles /stop  
```  
  
 /sub o /s  
 facoltativo. Effettua la ricerca nelle sottocartelle incluse nella directory specificata nell'argomento /lookin:`searchpath`.  
  
 /text2 o /2  
 facoltativo. Visualizza i risultati della sostituzione nella finestra **Risultati ricerca 2**.  
  
 /wild o /l  
 facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni per rappresentare un carattere o una sequenza di caratteri.  
  
 /word o /w  
 facoltativo. Cerca solo parole intere.  
  
## <a name="example"></a>Esempio  
 In questo esempio `btnCancel` viene cercato e sostituito con `btnReset` in tutti i file CLS presenti nella cartella "my visual studio projects" e le informazioni relative alle sostituzioni vengono visualizzate nella finestra **Risultati ricerca 2**.  
  
```  
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Ricerca e sostituzione di testo](../../ide/finding-and-replacing-text.md)   
 [Sostituisci nei file](../../ide/replace-in-files.md)   
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md) (Alias di comandi di Visual Studio)
