---
title: Comando Find | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 93ec728b6e7ab3a197382bbd66cb34906d248747
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="find-command"></a>Comando Trova
Esegue la ricerca di testo nei file usando un subset delle opzioni disponibili nella scheda **Cerca nei file** della finestra **Trova e sostituisci**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]   
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]  
```  
  
## <a name="arguments"></a>Argomenti  
 `findwhat`  
 Obbligatorio. Testo da cercare.  
  
## <a name="switches"></a>Opzioni  
 /case o /c  
 Parametro facoltativo. Vengono rilevate corrispondenze solo se i caratteri maiuscoli e minuscoli corrispondono esattamente a quelli specificati nell'argomento `findwhat`.  
  
 /doc o /d  
 Parametro facoltativo. Cerca solo nel documento corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.  
  
 /markall o /m  
 Parametro facoltativo. Inserisce un grafo per ogni riga che contiene una corrispondenza della ricerca all'interno del documento corrente.  
  
 /open o /o  
 Parametro facoltativo. Cerca in tutti i documenti aperti come se fossero un unico documento. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.  
  
 /options o /t  
 Parametro facoltativo. Visualizza l'elenco delle impostazioni correnti dell'opzione di ricerca e non esegue una ricerca.  
  
 /proc o /p  
 Parametro facoltativo. Cerca solo nella routine corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.  
  
 /reset o /e  
 Parametro facoltativo. Ripristina le impostazioni predefinite delle opzioni di ricerca e non esegue la ricerca.  
  
 /sel o /s  
 Parametro facoltativo. Cerca solo nella selezione corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open` o `/sel`.  
  
 /up o /u  
 Parametro facoltativo. Esegue la ricerca dalla posizione corrente nel file verso l'inizio del file. Per impostazione predefinita, le ricerche iniziano in corrispondenza della posizione nel file e procedono verso la fine del file.  
  
 /regex o /r  
 Parametro facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni che rappresentano modelli di testo anziché i caratteri letterali. Per l'elenco completo dei caratteri espressione regolare, vedere [Espressioni regolari](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 /wild o /l  
 Parametro facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni per rappresentare un carattere o una sequenza di caratteri.  
  
 /word o /w  
 Parametro facoltativo. Cerca solo parole intere.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene eseguita una ricerca con distinzione tra maiuscole e minuscole della parola "string" nella sezione di codice attualmente selezionata.  
  
```  
>Edit.Find somestring /sel /case  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md) (Alias di comandi di Visual Studio)