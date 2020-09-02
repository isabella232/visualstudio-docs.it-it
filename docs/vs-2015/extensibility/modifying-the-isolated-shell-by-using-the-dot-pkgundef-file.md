---
title: Modifica della shell isolata tramite. File Pkgundef | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eab02fe900e96ba37c63faae535974788f99ba78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538390"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Modifica della shell isolata tramite il file con estensione pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile modificare il file con estensione pkgundef in modo da escludere le voci del registro di sistema specificate da un'applicazione shell isolata. In genere, la prima volta che un'applicazione viene avviata in un computer, la shell di Visual Studio copia le voci del registro di sistema esistenti nella chiave radice del registro di sistema per l'applicazione. Sono inclusi tutti i riferimenti ai pacchetti VSPackage attualmente installati.  
  
 Per escludere una voce del registro di sistema specifica da un'applicazione shell isolata, aggiungere al file Application. pkgundef la chiave del pacchetto seguita dalla voce. Le chiavi e le voci sono rappresentate esattamente come nel file. pkgdef. ovvero, come [$RootKey $] o [$RootKey $ \\ *sottochiave*] e "*entry*" =*valore*, dove *sottochiave* è la sottochiave da influire, *entry* è la voce da rimuovere e *value* è `""` o `dword:00000000` .  
  
 Per escludere più voci da una chiave del registro di sistema, è sufficiente elencare la chiave una sola volta, seguito da una riga per ogni voce da escludere.  
  
 Per escludere un'intera chiave del registro di sistema da un'applicazione shell isolata, aggiungere la chiave al file Application. pkgundef, ma non specificare alcuna voce del registro di sistema per tale chiave.  
  
 È possibile aggiungere commenti al file con estensione pkgundef. Un commento a riga singola deve avere due barre come i primi due caratteri.  
  
 Ad esempio, per rimuovere i comandi di **connessione al database** e **Connetti per gestire r** dal menu **strumenti** , è possibile rimuovere il commento dalla riga:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 e aggiungere la riga:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 al file con estensione pkgundef dell'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [GUID del pacchetto delle funzionalità di Visual Studio](../extensibility/package-guids-of-visual-studio-features.md)   
 [Personalizzazione della shell isolata](../extensibility/customizing-the-isolated-shell.md)
