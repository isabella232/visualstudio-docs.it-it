---
title: Comando Aggiungi nuovo elemento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 952419c5dda9a64b0f3fde93fd314ed9b54fd1a7
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54835045"
---
# <a name="add-new-item-command"></a>Comando Aggiungi nuovo elemento
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Aggiunge un nuovo elemento, ad esempio un file con estensione htm, css o txt o una pagina con frame, alla soluzione corrente e lo apre.  
  
## <a name="syntax"></a>Sintassi  
  
```  
File.AddNewItem [filename] [/t:templatename] [/e:editorname]  
```  
  
## <a name="arguments"></a>Argomenti  
 `filename`  
 Facoltativo. Percorso e nome file dell'elemento da aggiungere alla soluzione.  
  
## <a name="switches"></a>Opzioni  
 /t: `templatename`  
 Facoltativo. Specifica il tipo di file da creare. Se non viene specificato alcun modello, per impostazione predefinita viene creato un file di testo.  
  
 La sintassi dell'argomento /t:`templatename` riflette le informazioni riportate nella finestra di dialogo **Aggiungi nuovo elemento di soluzione**. È necessario immettere il nome completo della categoria e il tipo di file separati da una barra rovesciata (`\`) racchiudendo l'intera stringa tra virgolette.  
  
 Ad esempio, per creare un nuovo file di testo, per l'argomento /t:`templatename` è necessario immettere quanto segue.  
  
```  
/t:"General\Style Sheet"  
```  
  
 /e: `editorname`  
 Facoltativo. Il nome dell'editor in cui verrà aperto il file. Se viene specificato l'argomento ma non viene fornito il nome di un editor, verrà visualizzata la finestra di dialogo **Apri con**.  
  
 La sintassi dell'argomento `editorname` usa i nomi degli editor così come visualizzati nella **finestra di dialogo Apri con**, racchiusi tra virgolette.  
  
 Ad esempio, per aprire un foglio di stile nell'editor del codice sorgente, per l'argomento /e:`editorname` è necessario immettere quanto segue.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="example"></a>Esempio  
 In questo esempio un nuovo elemento di soluzione, denominato MyHTMLpg, viene aggiunto alla soluzione corrente.  
  
```  
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
