---
redirect_url: shell/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file
title: Modifica la Shell isolata tramite il. File Pkgundef | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dfe0e4b39e96d98718ff98025add521a678699ac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Modifica la Shell isolata tramite il. File Pkgundef
È possibile modificare il file .pkgundef per escludere le voci del Registro di sistema da un'applicazione shell isolata. In genere, la prima volta che viene avviata un'applicazione in un computer, la shell di Visual Studio copia le voci del Registro di sistema di Visual Studio esistenti per la chiave del Registro di sistema radice per l'applicazione. Sono inclusi tutti i riferimenti ai pacchetti VSPackage attualmente installati.  
  
 Per escludere una voce del Registro di sistema da un'applicazione shell isolata, aggiungere la chiave del pacchetto aggiungendo la voce nel file di .pkgundef applicazione. Le chiavi e le voci sono rappresentate Analogamente al file. pkgdef. vale a dire come [$RootKey$] o [$ $RootKey\\*sottochiave*] e "*voce*" =*valore*, dove *sottochiave* è la sottochiave per influire sul, *voce* è la voce da rimuovere e *valore* è `""` o `dword:00000000`.  
  
 Per escludere più voci da una chiave del Registro di sistema, semplicemente elencare la chiave una sola volta, seguito da una riga per ogni voce da escludere.  
  
 Per escludere una chiave del Registro di sistema intero da un'applicazione shell isolata, aggiungere la chiave del file .pkgundef dell'applicazione, ma non tutte le voci del Registro di sistema per la chiave.  
  
 È possibile aggiungere commenti al file .pkgundef. Un commento a riga singola deve avere due barre come i primi due caratteri.  
  
 Ad esempio, per rimuovere il **Connetti al Database** e **Connetti al server r** i comandi nel **strumenti** menu, è possibile rimuovere il commento la riga:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 e aggiungere la riga:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 per il file dell'applicazione .pkgundef.  
  
## <a name="see-also"></a>Vedere anche  
 [GUID del pacchetto di funzionalità di Visual Studio](../extensibility/package-guids-of-visual-studio-features.md)   
 [Personalizzazione della shell isolata](../extensibility/customizing-the-isolated-shell.md)