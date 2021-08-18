---
title: Debug di applicazioni ASP.NET distribuite | Microsoft Docs
description: Usare Visual Studio per eseguire il debug di un'applicazione ASP.NET distribuita connettendosi al processo di lavoro e verificando che il debugger abbia accesso ai simboli per l'applicazione.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
ms.openlocfilehash: 0190d563dab26ee89a157cf4a997a53b8d8f3ae9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097609"
---
# <a name="debugging-deployed-aspnet-applications"></a>Debug di applicazioni ASP.NET distribuite
Per utilizzare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per eseguire il debug di un'applicazione distribuita, è necessario effettuare la connessione al processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] e verificare che il debugger abbia accesso ai simboli per l'applicazione. Inoltre, è necessario individuare e aprire i file di origine dell'applicazione. Per altre informazioni, vedere [Specify Symbol (.pdb) and Source Files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), How [to: Find the Name of the ASP.NET Process](../debugger/how-to-find-the-name-of-the-aspnet-process.md)e Requisiti di [sistema.](../debugger/aspnet-debugging-system-requirements.md)

> [!WARNING]
> Se ci si connette al processo di lavoro per il debug e si preme un punto di interruzione, tutto il codice gestito nel processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] si interrompe. L'arresto di tutto il codice gestito nel processo di lavoro può comportare l'arresto del lavoro per tutti gli utenti del server. Prima di eseguire il debug su un server di produzione, tenere in considerazione il potenziale impatto sulle attività produttive.

La connessione al processo di lavoro [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] è praticamente identica alla connessione a qualsiasi altro processo remoto. Dopo la connessione, se non è aperto il progetto corretto, al momento dell'interruzione dell'applicazione verrà visualizzata una finestra di dialogo. In questa finestra di dialogo è necessario immettere il percorso dei file di origine dell'applicazione. Il nome file specificato nella finestra di dialogo deve corrispondere a quello specificato nei simboli di debug, che si trovano sul server Web. Per altre informazioni, vedere [Connettersi a processi in esecuzione.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) Per configurare il debug remoto in IIS, vedere [Remote Debugging ASP.NET on a Remote IIS Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

> [!NOTE]
> Molte applicazioni Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] fanno riferimento a DLL contenenti logica di business o altro codice utile. Tale riferimento copia la DLL dal computer locale alla cartella \bin della directory virtuale dell'applicazione Web quando si distribuisce l'app. Quando si esegue il debug, tenere presente che l'applicazione Web fa riferimento a tale copia della DLL e non alla copia presente sul computer locale.

## <a name="see-also"></a>Vedi anche
- [Eseguire il debug ASP.NET applicazioni](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Come fare per: Attivare il debug per applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [Procedura: Trovare il nome del processo ASP.NET processo](../debugger/how-to-find-the-name-of-the-aspnet-process.md)
- [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)