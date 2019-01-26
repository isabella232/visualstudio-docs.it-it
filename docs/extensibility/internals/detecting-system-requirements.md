---
title: Rilevamento dei requisiti di sistema | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4df7ec753f1d636a74dfce74b451ecaf5557c53
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021676"
---
# <a name="detect-system-requirements"></a>Rilevare i requisiti di sistema
Un pacchetto VSPackage non può funzionare a meno che non è installato Visual Studio. Quando si usa Microsoft Windows Installer per gestire l'installazione del pacchetto VSPackage, è possibile configurare il programma di installazione per verificare se è installato Visual Studio. È anche possibile configurare e controllare il sistema per altri requisiti, ad esempio, una particolare versione di Windows o una determinata quantità di RAM.  
  
## <a name="detect-visual-studio-editions"></a>Rilevare le edizioni di Visual Studio  
 Per determinare se è installata un'edizione di Visual Studio, verificare che il valore della **installare** chiave del Registro di sistema viene *(REG_DWORD) 1* nella cartella appropriata, come elencato nella tabella seguente. Si noti che esiste una gerarchia di edizioni di Visual Studio:  
  
1.  Enterprise  
  
2.  Professionale  
  
3.  Community  
      
Quando si installa un'edizione più recente, le chiavi del Registro di sistema per tale edizione vengono aggiunti anche per quanto riguarda le versioni precedenti. Vale a dire, se è installata la versione Enterprise edition, il **installare** chiave è impostata su *1* per Enterprise, nonché per le edizioni Professional e Community. Pertanto, è necessario controllare solo per l'edizione più recente, che è necessario.  
  
> [!NOTE]
>  Nella versione a 64 bit dell'editor del Registro di sistema, chiavi a 32 bit vengono visualizzate nelle **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\**. Le chiavi di Visual Studio si trovano **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\**.  
  
|Prodotto|Chiave|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (integrata e isolata)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detect-when-visual-studio-is-running"></a>Rilevare quando viene eseguita da Visual Studio  
 Il pacchetto VSPackage non può essere registrato correttamente se Visual Studio è in esecuzione quando viene installato il pacchetto VSPackage. Il programma di installazione deve rilevare quando Visual Studio è in esecuzione e quindi rifiutare l'installazione del programma. Windows Installer non è possibile usare le voci della tabella per abilitare tale rilevamento. In alternativa, è necessario creare un'azione personalizzata, come indicato di seguito: Usare la `EnumProcesses` funzione per rilevare le *devenv.exe* elaborare e quindi impostare una proprietà di programma di installazione che viene usata in una condizione di avvio o Visualizza in modo condizionale una finestra di dialogo che chiede di chiudere Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Installare i pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)