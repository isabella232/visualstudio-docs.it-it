---
title: "Procedura: Includere i prerequisiti con un'applicazione ClickOnce | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcef749068dfb1f13e5b08160a70dda168b771ee
ms.sourcegitcommit: 36f5ffd6ae3215fe31837f4366158bf0d871f7a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2019
ms.locfileid: "59232853"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Procedura: Includere i prerequisiti con un'applicazione ClickOnce
Prima di poter distribuire i prerequisiti relativi al software con un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], è necessario scaricare i pacchetti di installazione per quei prerequisiti nel computer di sviluppo. Quando si pubblica un'applicazione e si sceglie **Scarica prerequisiti dallo stesso percorso dell'applicazione**, si verificherà un errore se i pacchetti di installazione non si trovano nella cartella **Pacchetti**.

> [!NOTE]
>  Per aggiungere un pacchetto di installazione di .NET Framework, vedere [Guida alla distribuzione di .NET Framework per sviluppatori](/dotnet/framework/deployment/deployment-guide-for-developers).

##  <a name="Package"></a> Per aggiungere un pacchetto di installazione tramite Package.xml

1. In Esplora file aprire la cartella **Pacchetti**.

    Per impostazione predefinita, il percorso è `%ProgramFiles(x86)%\Microsoft SDKs\ClickOnce Bootstrapper\Packages\`.

2. Aprire la cartella per il prerequisito che si desidera aggiungere e quindi aprire la cartella del linguaggio per la versione installata di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (ad esempio **en** per l'inglese).

3. Nel Blocco Note aprire il file*Package.xml*.

4. Individuare il **Name** elemento contenente **http://go.microsoft.com/fwlink**e copiare l'URL. Includere la parte **LinkID**.

   > [!NOTE]
   >  Se nessun **Name** elemento contiene **http://go.microsoft.com/fwlink**, aprire il **Product** file nella cartella radice del prerequisito e individuare il **fwlink** stringa.

   > [!IMPORTANT]
   >  Alcuni prerequisiti hanno più pacchetti di installazione (ad esempio, per sistemi a 32 bit o a 64 bit). Se più elementi **Nome** contengono **fwlink**, è necessario ripetere i passaggi restanti per ciascuno di essi.

5. Incollare l'URL nella barra degli indirizzi del proprio browser e, quando viene richiesto se eseguire o salvare, scegliere **Salva**.

    Questo passaggio consente di scaricare il file del programma di installazione nel computer.

6. Copiare il file nella cartella radice del prerequisito.

    Ad esempio, per il prerequisito di Windows Installer 4.5, copiare il file nella cartella *\Packages\WindowsInstaller4_5*.

    È ora possibile distribuire il pacchetto di installazione con la propria applicazione.

## <a name="see-also"></a>Vedere anche
- [Procedura: Installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
