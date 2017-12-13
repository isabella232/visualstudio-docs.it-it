---
title: Comando Sostituisci | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7201086ade629dc7c6d39039c088333be815cc26
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="replace-command"></a>Comando Sostituisci
Sostituisce il testo nei file usando un subset delle opzioni disponibili nella scheda **Sostituisci nei file** della finestra **Trova e sostituisci**.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Edit.Replace findwhat replacewith [/all] [/case]  
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]  
[/wild|/regex] [/word]  
```  
  
## <a name="arguments"></a>Argomenti  
 `findwhat`  
 Obbligatorio. Testo da cercare.  
  
 `replacewith`  
 Obbligatorio. Il testo di sostituzione per il testo corrispondente.  
  
## <a name="switches"></a>Opzioni  
 /all o /a  
 Parametro facoltativo. Sostituisce tutte le occorrenze del testo di ricerca con il testo di sostituzione.  
  
 /case o /c  
 Parametro facoltativo. Vengono rilevate corrispondenze quando i caratteri maiuscoli e minuscoli corrispondono esattamente a quelli specificati nell'argomento `findwhat`.  
  
 /doc o /d  
 Parametro facoltativo. Cerca solo il documento corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open`, o `/sel`.  
  
 /hidden o /h  
 Parametro facoltativo. Cerca il testo compresso e nascosto, come i metadati di un controllo DTC, un'area nascosta di un documento strutturato o un metodo o una classe compressi.  
  
 /open o /o  
 Parametro facoltativo. Cerca tutti i documenti aperti come se fossero un unico documento. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open`, o `/sel`.  
  
 /options o /t  
 Parametro facoltativo. Visualizza l'elenco delle impostazioni correnti dell'opzione di ricerca e non esegue una ricerca.  
  
 /proc o/p  
 Parametro facoltativo. Cerca solo la routine corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open`, o `/sel`.  
  
 /regex o /r  
 Parametro facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni che rappresentano modelli di testo anziché i caratteri letterali. Per l'elenco completo dei caratteri espressione regolare, vedere [Espressioni regolari](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 /reset o /e  
 Parametro facoltativo. Ripristina le impostazioni predefinite delle opzioni di ricerca e non esegue la ricerca.  
  
 /Sel o /s  
 Parametro facoltativo. Cerca solo la selezione corrente. Specificare solo uno degli ambiti di ricerca disponibili, `/doc`, `/proc`, `/open`, o `/sel`.  
  
 /up o /u  
 Parametro facoltativo. Esegue la ricerca dalla posizione corrente nel file verso la parte superiore del file. Per impostazione predefinita, le ricerche iniziano in corrispondenza della posizione del file e procedono verso la fine del file.  
  
 /wild o /l  
 Parametro facoltativo. Usa caratteri speciali predefiniti nell'argomento `findwhat` come notazioni per rappresentare un carattere o una sequenza di caratteri.  
  
 /word o /w  
 Parametro facoltativo. Cerca solo parole intere.  
  
## <a name="example"></a>Esempio  
 In questo esempio `btnSend` con `btnSubmit` tutti i documenti aperti.  
  
```  
>Edit.Replace btnSend btnSubmit /open  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Ricerca e sostituzione di testo](../../ide/finding-and-replacing-text.md)   
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md) (Alias di comandi di Visual Studio)