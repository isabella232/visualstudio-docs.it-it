---
title: Rilevamento dei requisiti di sistema | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
caps.latest.revision: 51
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 467554b8e50878bcdf1029e4792bbf168a09fa11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839423"
---
# <a name="detecting-system-requirements"></a>Rilevamento dei requisiti di sistema
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un pacchetto VSPackage non può funzionare a meno che non sia installato Visual Studio. Quando si usa Microsoft Windows Installer per gestire l'installazione del pacchetto VSPackage, è possibile configurare il programma di installazione per rilevare se Visual Studio è installato. È anche possibile configurarlo in modo da controllare il sistema per altri requisiti, ad esempio una particolare versione di Windows o una determinata quantità di RAM.  
  
## <a name="detecting-visual-studio-editions"></a>Rilevamento delle edizioni di Visual Studio  
 Per determinare se è installata un'edizione di Visual Studio, verificare che il valore della chiave install Registry sia (REG_DWORD) 1 nella cartella appropriata, come elencato nella tabella seguente. Si noti che è presente una gerarchia delle edizioni di Visual Studio:  
  
1. Enterprise  
  
2. Professionale  
  
3. Community  
  
   Quando viene installata un'edizione "superiore", vengono aggiunte le chiavi del registro di sistema per tale edizione e per le edizioni "inferiori". Ovvero, se Enterprise Edition è installato, la chiave di installazione è impostata su 1 per Enterprise, nonché per le edizioni Professional e community. È pertanto necessario verificare solo l'edizione "più elevata" necessaria.  
  
> [!NOTE]
> Nella versione a 64 bit dell'editor del registro di sistema, le chiavi a 32 bit vengono visualizzate in HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node \\ . Le chiavi di Visual Studio sono in HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing \\ .  
  
|Prodotto|Chiave|  
|-------------|---------|  
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|  
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|  
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|  
|Shell di Visual Studio 2015 (integrata e isolata)|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|  
  
## <a name="detecting-when-visual-studio-is-running"></a>Rilevamento quando Visual Studio è in esecuzione  
 Non è possibile registrare il pacchetto VSPackage correttamente se Visual Studio è in esecuzione durante l'installazione del pacchetto VSPackage. Il programma di installazione deve rilevare quando Visual Studio è in esecuzione e quindi rifiutare di installare il programma. Windows Installer non consente di utilizzare le voci di tabella per abilitare questo rilevamento. È invece necessario creare un'azione personalizzata, come indicato di seguito: usare la `EnumProcesses` funzione per rilevare il processo di devenv.exe e quindi impostare una proprietà del programma di installazione utilizzata in una condizione di avvio o visualizzare in modo condizionale una finestra di dialogo in cui viene richiesto all'utente di chiudere Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Installazione di pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
