---
title: Debug di applicazioni ASP.NET distribuite | Microsoft Docs
ms.date: 06/30/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 8d787e6586a9dcce2ca4d2c840f67e652bfc5714
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350550"
---
# <a name="debugging-deployed-aspnet-applications"></a>Debug di applicazioni ASP.NET distribuite
Per utilizzare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per eseguire il debug di un'applicazione distribuita, è necessario effettuare la connessione al processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e verificare che il debugger abbia accesso ai simboli per l'applicazione. Inoltre, è necessario individuare e aprire i file di origine dell'applicazione. Per altre informazioni, vedere [specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [procedura: trovare il nome del processo ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)e [requisiti di sistema](../debugger/aspnet-debugging-system-requirements.md).

> [!WARNING]
> Se ci si connette al [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] processo di lavoro per il debug e si raggiunge un punto di interruzione, tutto il codice gestito nel processo di lavoro si arresta. L'arresto di tutto il codice gestito nel processo di lavoro può comportare l'arresto del lavoro per tutti gli utenti del server. Prima di eseguire il debug su un server di produzione, tenere in considerazione il potenziale impatto sulle attività produttive.

La connessione al processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] è praticamente identica alla connessione a qualsiasi altro processo remoto. Dopo la connessione, se non è aperto il progetto corretto, al momento dell'interruzione dell'applicazione verrà visualizzata una finestra di dialogo. In questa finestra di dialogo è necessario immettere il percorso dei file di origine dell'applicazione. Il nome file specificato nella finestra di dialogo deve corrispondere a quello specificato nei simboli di debug, che si trovano sul server Web. Per ulteriori informazioni, vedere [Connetti a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md). Per configurare il debug remoto in IIS, vedere [Remote Debugging ASP.NET on a Remote IIS computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

> [!NOTE]
> Molte applicazioni Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] fanno riferimento a DLL contenenti logica di business o altro codice utile. Un riferimento di questo tipo copia la DLL dal computer locale alla cartella \bin della directory virtuale dell'applicazione Web quando si distribuisce l'app. Quando si esegue il debug, tenere presente che l'applicazione Web fa riferimento a tale copia della DLL e non alla copia presente sul computer locale.

## <a name="see-also"></a>Vedere anche
- [Eseguire il debug di applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Come fare per: Attivare il debug per applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Procedura: trovare il nome del processo ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)
- [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)