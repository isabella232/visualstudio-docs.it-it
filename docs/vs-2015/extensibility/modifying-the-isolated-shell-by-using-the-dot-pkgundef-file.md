---
title: Modifica della Shell isolata tramite il. File Pkgundef | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .pkgundef file
ms.assetid: 9cee2a20-f8ac-4d9d-aef9-068fcd9f27a4
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3741fc9abdae6693670538c80288dfdefcefd84e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519167"
---
# <a name="modifying-the-isolated-shell-by-using-the-pkgundef-file"></a>Modifica della Shell isolata tramite il. File Pkgundef
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [modificando l'isolato Shell tramite l'utilizzo di. File Pkgundef](https://docs.microsoft.com/visualstudio/extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgundef-file).  
  
È possibile modificare il file con estensione pkgundef per escludere le voci del Registro di sistema da un'applicazione shell isolata. In genere, la prima volta che un'applicazione viene avviata in un computer, la shell di Visual Studio copia le voci del Registro di sistema di Visual Studio esistente per la chiave del Registro di sistema radice per l'applicazione. Sono inclusi tutti i riferimenti ai pacchetti VSPackage attualmente installati.  
  
 Per escludere una voce del Registro di sistema da un'applicazione shell isolata, aggiungere al file con estensione pkgundef dell'applicazione la chiave del pacchetto aggiungendo la voce. Le chiavi e le voci sono rappresentate come in file con estensione pkgdef; vale a dire, come [$RootKey$] o [$ $RootKey\\*sottochiave*] e "*voce*" =*valore*, dove *sottochiave* è la sottochiave da assegnare, *movimento* è la voce da rimuovere, e *valore* sia `""` o `dword:00000000`.  
  
 Per escludere più voci da una chiave del Registro di sistema, semplicemente elencare la chiave di una sola volta, seguito da una riga per ogni voce da escludere.  
  
 Per escludere una chiave del Registro di sistema intero da un'applicazione shell isolata, aggiungere la chiave nel file con estensione pkgundef dell'applicazione ma non si specifica tutte le voci del Registro di sistema per la chiave.  
  
 È possibile aggiungere commenti al file con estensione pkgundef. Un commento a riga singola deve avere due barre come i primi due caratteri.  
  
 Ad esempio, per rimuovere il **Connetti al Database** e **Connetti al server r** i comandi nel **strumenti** menu, è possibile rimuovere il commento dalla riga di:  
  
```  
[$RootKey$\Packages\{8D8529D3-625D-4496-8354-3DAD630ECC1B}]  
```  
  
 e aggiungere la riga:  
  
```  
[$RootKey$\Packages\{198E76C1-34C0-424D-9957-B3EBD80265FB}]  
```  
  
 file con estensione pkgundef dell'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [GUID di pacchetto di funzionalità di Visual Studio](../extensibility/package-guids-of-visual-studio-features.md)   
 [Personalizzazione della shell isolata](../extensibility/customizing-the-isolated-shell.md)
