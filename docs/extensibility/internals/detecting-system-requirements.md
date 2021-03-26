---
title: Rilevamento dei requisiti di sistema | Microsoft Docs
description: Informazioni su come configurare il Microsoft Windows Installer per rilevare i requisiti di sistema, ad esempio l'edizione di Visual Studio installata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ffb00ca42376f8b7c150552c862bba7a24a5c1fb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056766"
---
# <a name="detect-system-requirements"></a>Rilevare i requisiti di sistema
Un pacchetto VSPackage non può funzionare a meno che non sia installato Visual Studio. Quando si usa Microsoft Windows Installer per gestire l'installazione del pacchetto VSPackage, è possibile configurare il programma di installazione per rilevare se Visual Studio è installato. È anche possibile configurarlo in modo da controllare il sistema per altri requisiti, ad esempio una particolare versione di Windows o una determinata quantità di RAM.

## <a name="detect-visual-studio-editions"></a>Rileva le edizioni di Visual Studio
 Per determinare se è installata un'edizione di Visual Studio, verificare che il valore della chiave **Install** Registry sia *(REG_DWORD) 1* nella cartella appropriata, come elencato nella tabella seguente. Si noti che è presente una gerarchia delle edizioni di Visual Studio:

1. Enterprise

2. Professionale

3. Community

Quando viene installata una versione più recente, vengono aggiunte le chiavi del registro di sistema per tale edizione e per le edizioni precedenti. Ovvero, se Enterprise Edition è installato, la chiave di **installazione** è impostata su *1* per Enterprise, nonché per le edizioni Professional e community. Pertanto, è necessario verificare solo la versione più recente richiesta.

> [!NOTE]
> Nella versione a 64 bit dell'editor del registro di sistema, le chiavi a 32 bit vengono visualizzate in **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\**. Le chiavi di Visual Studio sono **in \\HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing**.

|Prodotto|Chiave|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|
|Shell di Visual Studio 2015 (integrata e isolata)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Rileva quando Visual Studio è in esecuzione
 Non è possibile registrare il pacchetto VSPackage correttamente se Visual Studio è in esecuzione durante l'installazione del pacchetto VSPackage. Il programma di installazione deve rilevare quando Visual Studio è in esecuzione e quindi rifiutare di installare il programma. Windows Installer non consente di utilizzare le voci di tabella per abilitare questo rilevamento. È invece necessario creare un'azione personalizzata, come indicato di seguito: usare la `EnumProcesses` funzione per rilevare il processo di *devenv.exe* e quindi impostare una proprietà del programma di installazione utilizzata in una condizione di avvio o visualizzare in modo condizionale una finestra di dialogo in cui viene richiesto all'utente di chiudere Visual Studio.

## <a name="see-also"></a>Vedi anche
- [Installare VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
