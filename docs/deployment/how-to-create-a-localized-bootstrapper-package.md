---
title: 'Procedura: creare un pacchetto Bootstrapper localizzato | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1083633410c42c63f8c3e9a2ff341a2278f0b63a
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153215"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Procedura: creare un pacchetto bootstrapper localizzato
Dopo aver creato un pacchetto di programma di avvio automatico, è possibile creare versioni localizzate del pacchetto creando altri due file per ognuna delle impostazioni locali: file condizioni di una licenza di software (ad esempio un *EULA. RTF*) e un manifesto di pacchetto (*package. XML*).  
  
 Per impostazione predefinita, Visual Studio 2010 include i pacchetti localizzati del programma di avvio automatico solo per .NET Framework 4, .NET Framework 4 Client Profile, F# Runtime 2.0 e F# Runtime 4.0. È possibile creare pacchetti localizzati per altri programmi di avvio automatico completando tre passaggi.  
  
1.  Creare una cartella denominata dopo il nome delle impostazioni locali nel *\Programmi\Microsoft Sdks\windows\v7.0A\Bootstrapper\Packages.\\\<Nomepacchettoprogrammaavvioautomatico >*.  
  
2.  Creare un file contenente le condizioni di licenza software per il pacchetto del programma di avvio automatico e inserirlo nella nuova cartella.  
  
3.  Creare un manifesto di pacchetto denominato *package*, aggiornare le stringhe e le impostazioni cultura e inserire il file nella nuova cartella. Se è già stato creato un programma di bootstrap di Visual Studio nella lingua di destinazione, è possibile copiare di Visual Studio *package* file e modificarlo in questo passaggio.  
  
> [!NOTE]
>  Se si usa un progetto di installazione per distribuire le applicazioni, è possibile localizzare l'applicazione modificando la **localizzazione** proprietà.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-localized-bootstrapper-package"></a>Per creare un pacchetto localizzato del programma di avvio automatico  
  
1.  Creare una cartella denominata in base al nome delle impostazioni locali.  
  
     Nei computer a 32 bit creare la cartella nel *\Programmi\Microsoft Sdks\windows\v7.0A\Bootstrapper\Packages.\\\<Nomepacchettoprogrammaavvioautomatico >\\*  cartella.  
  
     Nei computer a 64 bit creare la cartella nel *\Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<Nomepacchettoprogrammaavvioautomatico >\\*  cartella.  
  
     La tabella seguente illustra i nomi di cartella che è possibile usare in base alle impostazioni locali.  
  
    |Impostazioni locali|Nome della cartella|  
    |------------|-----------------|  
    |Cinese (semplificato)|zh-Hans|  
    |Cinese (tradizionale)|zh-Hant|  
    |Ceco|cs|  
    |Tedesco|de|  
    |Inglese|en|  
    |Spagnolo|es|  
    |Francese|fr|  
    |Italiano|it|  
    |Coreano|ko|  
    |Giapponese|ja|  
    |Polacco|pl|  
    |Portoghese (Brasile)|pt-BR|  
    |Russo|ru|  
    |Turco|tr|  
  
2.  Creare un file contenente le condizioni di licenza software per il pacchetto del programma di avvio automatico e inserirlo nella nuova cartella.  
  
3.  Creare un manifesto di pacchetto denominato *package* e inserirlo nella nuova cartella. Per altre informazioni, vedere [procedura: creare un manifesto di pacchetto](../deployment/how-to-create-a-package-manifest.md).  
  
4.  Aggiornare la sezione `<Strings>` del manifesto di pacchetto in modo che le stringhe siano nella lingua appropriata per le impostazioni locali.  
  
5.  Cambiare il valore di `<String Name="Culture">` in modo che corrisponda al nome della cartella.  
  
6.  Salvare il *package* file.  
  
### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>Per creare un pacchetto del programma di avvio automatico per .NET Framework 3.5 Service Pack 1 localizzato in francese  
  
1.  Creare una cartella denominata *fr*. Il nome della cartella deve corrispondere al nome delle impostazioni locali.  
  
     Nei computer a 32 bit creare la cartella nel *\Programmi\Microsoft Sdks\windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1.\\*  cartella.  
  
     Nei computer a 64 bit creare la cartella nel *\Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\\*  cartella.  
  
2.  Inserire una versione localizzata delle condizioni di licenza software nel *fr* cartella.  
  
3.  Copia il *\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml file (x86) \Programmi* del file per il *fr* cartella e aprire il file nella finestra di progettazione XML.  
  
4.  Aggiornare la sezione `<Strings>` del manifesto di pacchetto in modo che le stringhe di errore siano in francese.  
  
5.  Modifica il `<String Name="Culture">` valore per *fr*.  
  
6.  Salvare il *package* file.  
  
## <a name="see-also"></a>Vedere anche  
 [Creare pacchetti di programma di avvio automatico](../deployment/creating-bootstrapper-packages.md)   
 [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)   
 [Procedura: Creare un manifesto di pacchetto](../deployment/how-to-create-a-package-manifest.md)