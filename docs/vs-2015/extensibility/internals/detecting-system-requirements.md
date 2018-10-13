---
title: Rilevamento dei requisiti di sistema | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 51
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e1956130203498d32d1ee39d67121f7797dd41fc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187476"
---
# <a name="detecting-system-requirements"></a>Rilevamento dei requisiti di sistema
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un pacchetto VSPackage non può funzionare a meno che non è installato Visual Studio. Quando si usa Microsoft Windows Installer per gestire l'installazione del pacchetto VSPackage, è possibile configurare il programma di installazione per verificare se è installato Visual Studio. È anche possibile configurare e controllare il sistema per altri requisiti, ad esempio, una particolare versione di Windows o una determinata quantità di RAM.  
  
## <a name="detecting-visual-studio-editions"></a>Individuazione di edizioni di Visual Studio  
 Per determinare se è installata un'edizione di Visual Studio, verificare che il valore della chiave del Registro di sistema di installazione è (REG_DWORD) 1 nella cartella appropriata, come indicato nella tabella seguente. Si noti che esiste una gerarchia di edizioni di Visual Studio:  
  
1.  Enterprise  
  
2.  Professionale  
  
3.  Community  
  
 Quando si installa un'edizione "più elevata", vengono aggiunte le chiavi del Registro di sistema per tale edizione anche per le edizioni "lower". Vale a dire, se è installata la versione Enterprise edition, la chiave di installazione è impostata su 1 per Enterprise, nonché per le edizioni Professional e Community. Pertanto è necessario controllare solo per l'edizione del "massimo" è necessario.  
  
> [!NOTE]
>  Nella versione a 64 bit dell'editor del Registro di sistema, chiavi a 32 bit vengono visualizzate in HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\. Le chiavi di Visual Studio sono sotto HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\\.  
  
|Prodotto|Chiave|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Visual Studio 2015 Shell (integrata e isolata)|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Rilevare quando viene eseguita da Visual Studio  
 Il pacchetto VSPackage non può essere registrato correttamente se Visual Studio è in esecuzione quando viene installato il pacchetto VSPackage. Il programma di installazione deve rilevare quando Visual Studio è in esecuzione e quindi rifiutare l'installazione del programma. Windows Installer non è possibile usare le voci della tabella per abilitare tale rilevamento. In alternativa, è necessario creare un'azione personalizzata, come indicato di seguito: uso di `EnumProcesses` funzione per rilevare devenv.exe exe e quindi impostare una proprietà di programma di installazione che viene usata in una condizione di avvio o in modo condizionale consente di visualizzare una finestra di dialogo che chiede di chiudere Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Installazione di pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

