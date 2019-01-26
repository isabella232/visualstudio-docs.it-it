---
title: Gestione dei componenti | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10d5654983de6ced572d60243a7744608b2c3f53
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031383"
---
# <a name="component-management"></a>Gestione dei componenti
Unità delle attività del programma di installazione di Windows sono definite come componenti di Windows Installer (talvolta denominati WICs o solo i componenti). Un GUID identifica ogni WIC, ovvero l'unità di base di conteggio dei riferimenti per le configurazioni che usano Windows Installer e installazione.  
  
 Sebbene sia possibile usare diversi prodotti per creare il programma di installazione di VSPackage, questa discussione si presuppone l'uso di Windows Installer (*file con estensione msi*) file. Quando si crea un programma di installazione, è necessario gestire correttamente la distribuzione del file in modo che il conteggio dei riferimenti corretto venga eseguita in qualsiasi momento. Di conseguenza, diverse versioni del prodotto non interferiscono con o smettono di funzionare tra loro in una combinazione di installare e disinstallare gli scenari.  
  
 Nel programma di installazione di Windows, il conteggio dei riferimenti si verifica a livello di componente. È necessario organizzare con attenzione le risorse, ovvero i file, voci del Registro di sistema e così via, ovvero in componenti. Esistono altri livelli di organizzazione, quali moduli, le funzionalità e i prodotti, che possono aiutare in scenari diversi. Per altre informazioni, vedere [nozioni di base di Windows Installer](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Linee guida del programma di installazione per l'installazione side-by-side di creazione  
  
-   Creare file e le chiavi del Registro di sistema che vengono condivise tra le versioni nei propri componenti.  
  
     In questo modo consente di renderli facilmente nella prossima versione. Ad esempio, le librerie dei tipi registrati a livello globale, estensioni di file, altri elementi registrati in **HKEY_CLASSES_ROOT**e così via.  
  
-   Raggruppare i componenti condivisi in moduli unione separato.  
  
     Questa strategia consente di modificare in modo corretto per l'installazione side-by-side in futuro.  
  
-   Installare i file condivisi e le chiavi del Registro di sistema utilizzando gli stessi componenti di Windows Installer in tutte le versioni.  
  
     Se si usa un componente diverso, i file e le voci del Registro di sistema vengono disinstallate quando si disinstalla un pacchetto VSPackage con controllo delle versioni, ma è ancora installato un altro pacchetto VSPackage.  
  
-   Non combinare gli elementi condivisi e con controllo delle versioni nello stesso componente.  
  
     Questa operazione rende Impossibile installare gli elementi condivisi a un percorso globale e gli elementi con controllo delle versioni da percorsi di tipo isolati.  
  
-   Non dispongono di chiavi del Registro di sistema condivise che puntano ai file con controllo delle versioni.  
  
     Se esegue l'operazione, le chiavi condivise verranno sovrascritto quando viene installato un altro pacchetto VSPackage con controllo delle versioni. Dopo aver rimosso la seconda versione, il file a cui punta la chiave è più presente.  
  
## <a name="see-also"></a>Vedere anche  
 [Scegliere tra pacchetti VSPackage condivisi e con controllo delle versioni](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Scenari di installazione di VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)