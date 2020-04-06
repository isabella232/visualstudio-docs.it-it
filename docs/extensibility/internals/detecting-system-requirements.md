---
title: Rilevamento dei requisiti di sistema Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ab254df5d53f379704128d8860b8d7fe5655bae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708730"
---
# <a name="detect-system-requirements"></a>Rilevare i requisiti di sistema
Un VSPackage non può funzionare a meno che non è installato Visual Studio.A VSPackage cannot function unless Visual Studio is installed. Quando si utilizza Microsoft Windows Installer per gestire l'installazione del pacchetto VSPackage, è possibile configurare il programma di installazione per rilevare se Visual Studio è installato. È inoltre possibile configurarlo per controllare il sistema per altri requisiti, ad esempio, una particolare versione di Windows o una particolare quantità di RAM.

## <a name="detect-visual-studio-editions"></a>Rilevare le edizioni di Visual StudioDetect Visual Studio editions
 Per determinare se è installata un'edizione di Visual Studio, verificare che il valore della chiave del Registro di sistema **Install** sia *(REG_DWORD) 1* nella cartella appropriata, come elencato nella tabella seguente. Si noti che esiste una gerarchia di edizioni di Visual Studio:Note that there is a hierarchy of Visual Studio editions:

1. Enterprise

2. Professionale

3. Community

Quando viene installata un'edizione più recente, vengono aggiunte le chiavi del Registro di sistema per tale edizione, nonché per le edizioni precedenti. In altre parti, se è installata l'edizione Enterprise, la chiave di **installazione** è impostata su *1* per Enterprise, nonché per le edizioni Professional e Community. Pertanto, è necessario controllare solo per l'edizione più recente necessaria.

> [!NOTE]
> Nella versione a 64 bit dell'editor del Registro di sistema, le chiavi a 32 bit vengono visualizzate in **HKEY_LOCAL_MACHINE SOFTWARE\\Wow6432Node**. Le chiavi di Visual Studio si trovano in **HKEY_LOCAL_MACHINE SOFTWARE, Wow6432Node, Microsoft DevDiv, vs, Servicing\\**.

|Prodotto|Chiave|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE SOFTWARE , Microsoft DevDiv , vs , servicing 14.0 , enterprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE SOFTWARE Microsoft DevDiv vs , Servicing 14.0 , professionale|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE software Microsoft DevDiv vs|
|Visual Studio 2015 Shell (integrato e isolato)|HKEY_LOCAL_MACHINE'ISShell di HKEY_LOCAL_MACHINE SOFTWARE|

## <a name="detect-when-visual-studio-is-running"></a>Rileva quando Visual Studio è in esecuzione
 Il pacchetto VSPackage non può essere registrato correttamente se Visual Studio è in esecuzione quando è installato il pacchetto VSPackage. Il programma di installazione deve rilevare quando Visual Studio è in esecuzione e quindi rifiutare di installare il programma. Windows Installer non consente di utilizzare le voci di tabella per abilitare tale rilevamento. Al contrario, è necessario creare un'azione personalizzata, come indicato di seguito: utilizzare la `EnumProcesses` funzione per rilevare il processo *devenv.exe* e quindi impostare una proprietà del programma di installazione utilizzata in una condizione di avvio o visualizzare in modo condizionale una finestra di dialogo che richiede all'utente di chiudere Visual Studio.

## <a name="see-also"></a>Vedere anche
- [Installare i pacchetti VSPackage con Windows InstallerInstall VSPackages With Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
