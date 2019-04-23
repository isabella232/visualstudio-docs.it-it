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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60090446"
---
# <a name="component-management"></a>Gestione dei componenti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Unità delle attività del programma di installazione di Windows sono definite come componenti di Windows Installer (talvolta denominati WICs o solo i componenti). Un GUID identifica ogni WIC, ovvero l'unità di base di conteggio dei riferimenti per le configurazioni che usano Windows Installer e installazione.  
  
 Sebbene sia possibile usare diversi prodotti per creare il programma di installazione di VSPackage, questa discussione si presuppone l'uso di file Windows Installer (MSI). Quando si crea un programma di installazione, è necessario gestire correttamente la distribuzione del file in modo che il conteggio dei riferimenti corretto venga eseguita in qualsiasi momento. Di conseguenza, diverse versioni del prodotto non interferiscono con o smettono di funzionare tra loro in una combinazione di installare e disinstallare gli scenari.  
  
 Nel programma di installazione di Windows, il conteggio dei riferimenti si verifica a livello di componente. È necessario organizzare con attenzione le risorse, ovvero i file, voci del Registro di sistema e così via, ovvero in componenti. Esistono altri livelli di organizzazione, quali moduli, le funzionalità e i prodotti, che possono aiutare in scenari diversi. Per altre informazioni, vedere [nozioni di base di Windows Installer](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Linee guida del programma di installazione per l'installazione Side-by-side di creazione  
  
- Creare file e le chiavi del Registro di sistema che vengono condivise tra le versioni nei propri componenti.  
  
     In questo modo è possibile renderli facilmente nella prossima versione. Librerie dei tipi registrati a livello globale, ad esempio i file delle estensioni, gli altri elementi registrati in HKEY_CLASSES_ROOT e così via.  
  
- Raggruppare i componenti condivisi in moduli unione separato.  
  
     In questo modo si creano in modo corretto per lo spostamento in avanti side-by-side.  
  
- Installare i file condivisi e le chiavi del Registro di sistema utilizzando gli stessi componenti di Windows Installer in tutte le versioni.  
  
     Se si usa un componente diverso, i file e le voci del Registro di sistema vengono disinstallate quando si disinstalla un pacchetto VSPackage con controllo delle versioni, ma è ancora installato un altro pacchetto VSPackage.  
  
- Non combinare gli elementi condivisi e con controllo delle versioni nello stesso componente.  
  
     Questa operazione rende Impossibile installare gli elementi condivisi a un percorso globale e gli elementi con controllo delle versioni da percorsi di tipo isolati.  
  
- Non dispongono di chiavi del Registro di sistema condivise che puntano ai file con controllo delle versioni.  
  
     Se esegue l'operazione, le chiavi condivise verranno sovrascritto quando viene installato un altro pacchetto VSPackage con controllo delle versioni. Dopo aver rimosso la seconda versione, il file a cui punta la chiave è più presente.  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta tra pacchetti VSPackage condivisi e con controllo delle versioni](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Scenari di installazione di pacchetti VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)
