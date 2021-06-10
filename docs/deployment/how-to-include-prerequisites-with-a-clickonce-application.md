---
title: Includi prerequisiti (app ClickOnce)
description: Informazioni su come ottenere i pacchetti del programma di installazione per i prerequisiti da distribuire per l'applicazione ClickOnce per il computer di sviluppo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b41529182b7cca8cea8f94206601b7a818d35420
ms.sourcegitcommit: 6aa55db5e1fe19d4d17886e0bfe140dbd186f8ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/10/2021
ms.locfileid: "111877741"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Procedura: Includere i prerequisiti con un'applicazione ClickOnce
Prima di poter distribuire i prerequisiti relativi al software con un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], è necessario scaricare i pacchetti di installazione per quei prerequisiti nel computer di sviluppo. Quando si pubblica un'applicazione e si sceglie **Scarica prerequisiti dallo stesso percorso dell'applicazione**, si verificherà un errore se i pacchetti di installazione non si trovano nella cartella **Pacchetti**.

> [!NOTE]
> Per aggiungere un pacchetto di installazione per il .NET Framework, vedere .NET Framework [Deployment Guide for Developers](/dotnet/framework/deployment/deployment-guide-for-developers).

## <a name="to-add-an-installer-package-by-using-packagexml"></a><a name="Package"></a> Per aggiungere un pacchetto di installazione tramite Package.xml

1. In Esplora file aprire la cartella **Pacchetti**.

    Per impostazione predefinita, il percorso è `%ProgramFiles(x86)%\Microsoft SDKs\ClickOnce Bootstrapper\Packages\` .

>[!NOTE]
> A partire dalla versione Visual Studio 2019 Update 7, i pacchetti del programma di avvio automatico verranno individuati anche nel percorso *<VS Install Path> \MSBuild\Microsoft\VisualStudio\BootstrapperPackages*.

2. Aprire la cartella per il prerequisito che si desidera aggiungere e quindi aprire la cartella del linguaggio per la versione installata di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (ad esempio **en** per l'inglese).

3. Nel Blocco Note aprire il file *Package.xml*.

4. Individuare **l'elemento** Name che contiene `http://go.microsoft.com/fwlink` e copiare l'URL. Includere la parte **LinkID**.

   > [!NOTE]
   > Se nessun **elemento Name** contiene , aprire il fileProduct.xmlnella cartella radice per il prerequisito e `http://go.microsoft.com/fwlink` individuare la stringa **fwlink.** 

   > [!IMPORTANT]
   > Alcuni prerequisiti hanno più pacchetti di installazione (ad esempio, per sistemi a 32 bit o a 64 bit). Se più elementi **Nome** contengono **fwlink**, è necessario ripetere i passaggi restanti per ciascuno di essi.

5. Incollare l'URL nella barra degli indirizzi del proprio browser e, quando viene richiesto se eseguire o salvare, scegliere **Salva**.

    Questo passaggio consente di scaricare il file del programma di installazione nel computer.

6. Copiare il file nella cartella radice del prerequisito.

    Ad esempio, per il .NET Framework 4.7.2, copiare il file nella *cartella \Packages\DotNetFX472.*

    È ora possibile distribuire il pacchetto di installazione con la propria applicazione.

## <a name="see-also"></a>Vedi anche
- [Procedura: Installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
