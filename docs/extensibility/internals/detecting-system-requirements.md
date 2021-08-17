---
title: Rilevamento dei requisiti di sistema | Microsoft Docs
description: Informazioni su come configurare il programma di installazione di Microsoft Windows per rilevare i requisiti di sistema, ad esempio l'edizione Visual Studio installata.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 09c83eabb15c1ba4573bc35925529f46d4fb9ad6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069965"
---
# <a name="detect-system-requirements"></a>Rilevare i requisiti di sistema
Un VSPackage non può funzionare a meno Visual Studio installato. Quando si usa Microsoft Windows Installer per gestire l'installazione del pacchetto VSPackage, è possibile configurare il programma di installazione per rilevare se Visual Studio installato. È anche possibile configurarlo per verificare la presenza di altri requisiti nel sistema, ad esempio una versione specifica Windows o una particolare quantità di RAM.

## <a name="detect-visual-studio-editions"></a>Rilevare Visual Studio edizioni
 Per determinare se è installata un'edizione di Visual Studio, verificare che il valore della chiave del Registro di sistema Install *sia (REG_DWORD) 1* nella cartella appropriata, come elencato nella tabella seguente.  Si noti che esiste una gerarchia di Visual Studio edizioni:

1. Enterprise

2. Professionale

3. Community

Quando viene installata una versione più recente, vengono aggiunte le chiavi del Registro di sistema per tale edizione, nonché per le edizioni precedenti. In altri Enterprise, se è installata  l'edizione Enterprise, la chiave di installazione è impostata su *1* per Enterprise, nonché per le edizioni Professional e Community. Pertanto, è necessario verificare solo l'edizione più recente necessaria.

> [!NOTE]
> Nella versione a 64 bit dell'editor del Registro di sistema le chiavi a 32 bit vengono visualizzate **inHKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\**. Le Visual Studio sono in **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\**.

|Prodotto|Chiave|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|
|Visual Studio 2015 Shell (integrata e isolata)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Rilevare quando Visual Studio è in esecuzione
 Il pacchetto VSPackage non può essere registrato correttamente se Visual Studio è in esecuzione quando il pacchetto VSPackage è installato. Il programma di installazione deve rilevare quando Visual Studio è in esecuzione e quindi rifiutare l'installazione del programma. Windows Il programma di installazione non consente di usare voci di tabella per abilitare tale rilevamento. È invece necessario creare un'azione personalizzata, come indicato di seguito: Usare la funzione per rilevare il processodevenv.exee quindi impostare una proprietà del programma di installazione usata in una condizione di avvio o visualizzare in modo condizionale una finestra di dialogo che richiede all'utente di chiudere il `EnumProcesses` Visual Studio. 

## <a name="see-also"></a>Vedi anche
- [Installare VSPackage con il Windows di installazione](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
