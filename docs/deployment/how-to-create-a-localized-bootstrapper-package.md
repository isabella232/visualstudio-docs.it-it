---
title: 'Procedura: creare un pacchetto Bootstrapper localizzato | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbd9aab09d4972e5fe9c1784aed7cadf15c3db4c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611165"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Procedura: Creare un pacchetto localizzato del programma di avvio automatico
Dopo aver creato un pacchetto del programma di avvio automatico, è possibile creare versioni localizzate del pacchetto creando altri due file per ognuna delle impostazioni locali, ovvero un file per le condizioni di licenza software (ad esempio *eula.rtf*) e un manifesto di pacchetto (*package.xml*).

 Per impostazione predefinita, Visual Studio 2010 include i pacchetti localizzati del programma di avvio automatico solo per .NET Framework 4, .NET Framework 4 Client Profile, F# Runtime 2.0 e F# Runtime 4.0. È possibile creare pacchetti localizzati per altri programmi di avvio automatico completando tre passaggi.

1.  Creare una cartella denominata dopo il nome delle impostazioni locali nel *\Programmi\Microsoft Sdks\windows\v7.0A\Bootstrapper\Packages.\\\<Nomepacchettoprogrammaavvioautomatico >*.

2.  Creare un file contenente le condizioni di licenza software per il pacchetto del programma di avvio automatico e inserirlo nella nuova cartella.

3.  Creare un manifesto di pacchetto denominato *package.xml*, aggiornare le stringhe e le impostazioni cultura e quindi inserire il file nella nuova cartella. Se è già stato creato un programma di avvio automatico di Visual Studio nella lingua di destinazione, è possibile copiare il file *package.xml* di Visual Studio e modificarlo in questo passaggio.

> [!NOTE]
>  Se si intende usare un progetto di installazione per la distribuzione delle applicazioni, è possibile localizzare l'applicazione modificando la proprietà **Localization**.

 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-localized-bootstrapper-package"></a>Per creare un pacchetto localizzato del programma di avvio automatico

1.  Creare una cartella denominata in base al nome delle impostazioni locali.

     Nei computer a 32 bit creare la cartella nel *\Programmi\Microsoft Sdks\windows\v7.0A\Bootstrapper\Packages.\\\<Nomepacchettoprogrammaavvioautomatico >\\*  cartella.

     Nei computer a 64 bit creare la cartella nel *\Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\\\<Nomepacchettoprogrammaavvioautomatico >\\*  cartella.

     La tabella seguente illustra i nomi di cartella che è possibile usare in base alle impostazioni locali.

    |Impostazioni locali|Nome cartella|
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

3.  Creare un manifesto di pacchetto denominato *package.xml* e inserirlo nella nuova cartella. Per altre informazioni, vedere [procedura: creare un manifesto di pacchetto](../deployment/how-to-create-a-package-manifest.md).

4.  Aggiornare la sezione `<Strings>` del manifesto di pacchetto in modo che le stringhe siano nella lingua appropriata per le impostazioni locali.

5.  Cambiare il valore di `<String Name="Culture">` in modo che corrisponda al nome della cartella.

6.  Salvare il file *package.xml*.

### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>Per creare un pacchetto del programma di avvio automatico per .NET Framework 3.5 Service Pack 1 localizzato in francese

1.  Creare una cartella denominata *fr*. Il nome della cartella deve corrispondere al nome delle impostazioni locali.

     Nei computer a 32 bit creare la cartella in *\Programmi\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\\\*.

     Nei computer a 64 bit creare la cartella in *\Programmi (x86)\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\\\*.

2.  Inserire una versione localizzata delle condizioni di licenza software nella cartella *fr*.

3.  Copiare il file *\Programmi (x86)\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml* nella cartella *fr* e aprirlo in Progettazione XML.

4.  Aggiornare la sezione `<Strings>` del manifesto di pacchetto in modo che le stringhe di errore siano in francese.

5.  Cambiare il valore di `<String Name="Culture">` in *fr*.

6.  Salvare il file *package.xml*.

## <a name="see-also"></a>Vedere anche
- [Creare pacchetti del programma di avvio automatico personalizzati](../deployment/creating-bootstrapper-packages.md)
- [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)
- [Procedura: Creare un manifesto di pacchetto](../deployment/how-to-create-a-package-manifest.md)