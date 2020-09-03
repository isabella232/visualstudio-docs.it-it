---
title: Gestione dei componenti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 56a110f382d0b182eed0ea1a95cd4dabf2877037
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191861"
---
# <a name="component-management"></a>Gestione dei componenti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le unità di attività nel Windows Installer sono definite componenti Windows Installer (talvolta denominati WICs o Just Components). Un GUID identifica ogni WIC, ovvero l'unità di base dell'installazione e il conteggio dei riferimenti per le configurazioni che utilizzano Windows Installer.  
  
 Sebbene sia possibile usare diversi prodotti per creare il programma di installazione di VSPackage, questa discussione presuppone l'uso di file di Windows Installer (MSI). Quando si crea il programma di installazione, è necessario gestire correttamente la distribuzione di file in modo che il conteggio dei riferimenti corretto avvenga sempre. Di conseguenza, diverse versioni del prodotto non interferiscono o si interromperanno tra loro in una combinazione di scenari di installazione e disinstallazione.  
  
 In Windows Installer, il conteggio dei riferimenti viene eseguito a livello di componente. È necessario organizzare con attenzione le risorse, ovvero file, voci del registro di sistema e così via, in componenti. Esistono altri livelli di organizzazione, ad esempio moduli, funzionalità e prodotti, che possono essere utili in scenari diversi. Per ulteriori informazioni, vedere [nozioni di base su Windows Installer](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Linee guida per la creazione dell'installazione side-by-side  
  
- Creare file e chiavi del registro di sistema condivisi tra le versioni nei propri componenti.  
  
     In questo modo è possibile utilizzarli facilmente nella versione successiva. Ad esempio, le librerie dei tipi registrate globalmente, le estensioni di file, altri elementi registrati in HKEY_CLASSES_ROOT e così via.  
  
- Raggruppare i componenti condivisi in moduli unione distinti.  
  
     Questo consente di creare correttamente per lo sviluppo affiancato.  
  
- Installare i file condivisi e le chiavi del registro di sistema usando gli stessi componenti Windows Installer tra le versioni.  
  
     Se si usa un componente diverso, i file e le voci del registro di sistema vengono disinstallati quando viene disinstallato un pacchetto VSPackage con versione, ma è ancora installato un altro pacchetto VSPackage.  
  
- Non combinare elementi condivisi e con versione nello stesso componente.  
  
     In questo modo è Impossibile installare gli elementi condivisi in un percorso globale e gli elementi con controllo delle versioni in posizioni isolate.  
  
- Non sono disponibili chiavi del registro di sistema condivise che puntano a file con versione.  
  
     In tal caso, le chiavi condivise verranno sovrascritte quando viene installato un altro pacchetto VSPackage con versione. Dopo la rimozione della seconda versione, il file a cui punta la chiave non è più disponibile.  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta tra VSPackage condivisi e con versione](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Scenari di installazione di pacchetti VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)
