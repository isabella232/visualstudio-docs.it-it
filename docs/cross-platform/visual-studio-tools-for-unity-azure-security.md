---
title: Visual Studio Tools per Unity - Procedura dettagliata di Azure - Protezione | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: F4FD6E1C-EA64-4613-BDDE-6E4E5CCF983E
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 1ffb0c57329a8453208978cee69daa771d8ee0e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="update-unity-mono-security-certificate-store"></a>Aggiornare l'archivio certificati di protezione di Mono di Unity

Mono di Unity ha in dotazione un archivio certificati vuoto e pertanto non considera attendibile alcun sito. Per altre informazioni, vedere le [domande frequenti sulla protezione di Mono ](http://www.mono-project.com/docs/faq/security/).

Per connettersi ad Azure senza ignorare il protocollo TLS/SSL, è necessario aggiornare l'archivio certificati di Mono di Unity.

## <a name="using-mozroots-to-install-certificates"></a>Installazione di certificati tramite mozroots

Lo strumento mozroots, incluso in Mono, consente di scaricare e installare l'elenco di certificati radice di Mozilla.

1. Aprire il terminale del prompt dei comandi.

2. All'interno di terminale passare alla directory **C:\Programmi\Unity\Editor\Data\MonoBleedingEdge\bin>**. Il percorso esatto può cambiare in base al percorso di installazione di Unity nel computer locale.

3. Digitare il comando seguente e premere **Invio** per eseguirlo:

  `mono ..\lib\mono\4.5\mozroots.exe --sync --import`

4. Si otterrà l'output seguente. Il numero di certificati aggiunti può essere diverso:

  ```
  Downloading from 'https://hg.mozilla.org/releases/mozilla-release/raw-file/default/security/nss/lib/ckfw/builtins/certdata.txt'...
  Importing certificates into user store...
  1 new root certificates were added to your trust store.
  Import process completed.
  ```

5. È ora possibile eseguire il progetto di esempio senza ricevere errori correlati al protocollo TLS.

## <a name="next-step"></a>Passaggio successivo

* [Testare la connessione client](visual-studio-tools-for-unity-azure-connection.md)
