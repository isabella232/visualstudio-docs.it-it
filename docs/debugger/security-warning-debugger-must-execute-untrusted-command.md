---
title: 'Avviso di sicurezza: Il Debugger deve eseguire un comando non attendibile | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c4ab45feeae409a1951e1a57e964eaaa5963896
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56690354"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Avviso di sicurezza: il debugger deve eseguire un comando non attendibile
Questa finestra di dialogo di avviso viene visualizzata quando si usa il server di origine. Indica che il comando che deve essere eseguito dal debugger per ottenere il codice sorgente non è incluso nell'elenco dei comandi attendibili per il server di origine contenuto nel file srcsvr.ini. Se il comando è valido, è possibile aggiungerlo al file srcsvr.ini. In caso contrario, è opportuno non eseguirlo. Per altre informazioni, vedere [Specifica di file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="message-text"></a>Testo del messaggio
 **Il debugger deve eseguire il seguente comando non attendibile per ottenere il codice sorgente dal server di origine.**

 **Se il file del simbolo di debug (\*.pdb) non proviene da un'origine conosciuta e attendibile, questo comando potrebbe essere non valido o pericoloso da eseguire.**

 **Eseguire il comando?**

## <a name="uielement-list"></a>Elenco UIElement
 Finestra di comando di testo dal file con estensione PDB per l'esecuzione.

 Consenti esecuzione comando da eseguire.

 Non eseguire arrestare l'esecuzione del comando e il download del file dal Server di origine.

## <a name="see-also"></a>Vedere anche
- [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Server di origine](/windows/desktop/Debug/source-server-and-source-indexing)