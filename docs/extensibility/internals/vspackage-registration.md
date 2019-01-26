---
title: Registrazione di pacchetti VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09433968c8a735538ce276c854a38449735c2045
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2019
ms.locfileid: "55043622"
---
# <a name="vspackage-registration"></a>Registrazione di pacchetti VSPackage
È necessario consigliare i pacchetti VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che sono installati e deve essere caricato. Questo processo viene eseguito scrivendo informazioni nel Registro di sistema. Ovvero un tipico processo di un programma di installazione.  
  
> [!NOTE]
>  È una prassi durante lo sviluppo di VSPackage per usare registrazione automatica. Tuttavia, [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] partner non può essere rilasciato i prodotti tramite registrazione automatica come parte del programma di installazione.  
  
 Le voci del Registro di sistema in un pacchetto Windows Installer vengono in genere stabilite nella tabella del Registro di sistema. È anche possibile registrare le estensioni di file nella tabella del Registro di sistema. Tuttavia, programma di installazione di Windows fornisce supporto incorporato tramite il ProgId (programmatic identifier), classe, estensione e le tabelle di verbo. Per altre informazioni, vedere [tabelle di Database](/windows/desktop/Msi/database-tables).  
  
 Assicurarsi che le voci del Registro di sistema sono associate il componente che è appropriato per la strategia side-by-side scelta. Ad esempio, le voci del Registro di sistema per un file condiviso devono essere associate a Windows Installer componente quel file. Allo stesso modo, le voci del Registro di sistema per un file specifico della versione devono essere associate a componente quel file. In caso contrario, installare o disinstallare il pacchetto VSPackage per una versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] potrebbe interrompere il pacchetto VSPackage in altre versioni. Per altre informazioni, vedere [che supporta più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  Il modo più semplice per gestire la registrazione è usare gli stessi dati negli stessi file per la registrazione per gli sviluppatori e registrazione in fase di installazione. Ad esempio, alcuni strumenti di sviluppo di programma di installazione possono utilizzare file in formato con estensione reg in fase di compilazione. Se gli sviluppatori di gestire i file con estensione reg per i propri sviluppo quotidiane e il debug, tali file possono essere inclusi nel programma di installazione automaticamente. Se non è possibile condividere automaticamente i dati di registrazione, è necessario assicurarsi che la copia del programma di installazione dei dati di registrazione è aggiornata.  
  
## <a name="registering-unmanaged-vspackages"></a>Registrazione di pacchetti VSPackage non gestiti  
 Pacchetti VSPackage non gestiti (incluse quelle generate dal modello di pacchetto Visual Studio) usano i file con estensione RGS stile ATL per archiviare le informazioni di registrazione. Il formato del file con estensione RGS è specifico di ATL e non può essere utilizzato in genere come-è tramite un'installazione di authoring tool. Informazioni di registrazione per il programma di installazione di VSPackage devono essere gestite separatamente. Ad esempio, gli sviluppatori possono mantenere file nel formato con estensione reg sincronizzato con RGS le modifiche ai file. I file con estensione reg possono essere uniti con RegEdit per progetti di sviluppo o utilizzati da un programma di installazione.  
  
## <a name="registering-managed-vspackages"></a>La registrazione di pacchetti VSPackage gestiti  
 Lo strumento RegPkg legge gli attributi di registrazione da un pacchetto VSPackage gestito e sia possibile scrivere le informazioni direttamente al Registro di sistema o la scrittura di file con estensione reg-formato che può essere utilizzata da un programma di installazione.  
  
> [!NOTE]
>  Lo strumento RegPkg non è ridistribuibile e non può essere usato per registrare un VSPackage di sistema dell'utente.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Il motivo per cui i pacchetti VSPackage devono non effettuare la registrazione automatica al momento dell'installazione  
 I programmi di installazione del pacchetto VSPackage non basarsi su registrazione automatica. A prima vista, mantenendo i valori del Registro di sistema di un pacchetto VSPackage solo in VSPackage se stessa dovrebbe essere una buona idea. Dato che gli sviluppatori sono necessari i valori del Registro di sistema disponibili per il proprio lavoro routine e di test, è opportuno evitare di mantenere una copia separata dei dati del Registro di sistema nel programma di installazione. Il programma di installazione può basarsi sul VSPackage per scrivere i valori del Registro di sistema.  
  
 Pur good in teoria, registrazione automatica presenta alcuni difetti che rendono non idoneo per l'installazione di VSPackage:  
  
- Corretto supporto di installazione, disinstallazione, rollback dell'installazione e disinstallazione rollback è necessario creare quattro azioni personalizzate per ogni pacchetto VSPackage gestito che esegue la registrazione automatica mediante la chiamata a RegPkg.  
  
- L'approccio adottato per il supporto side-by-side potrebbe richiedere che si creano quattro azioni personalizzate che richiamano RegSvr32 o RegPkg per ogni versione supportata di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
- Un'installazione con i moduli di registrazione automatica non può essere annullata in modo sicuro perché non è possibile indicare se le chiavi di registrazione automatica vengono usate da un'altra funzionalità o l'applicazione.  
  
- DLL self-registrata link talvolta alle DLL ausiliari che non sono presenti o sono una versione errata. Al contrario, programma di installazione di Windows possono registrare le DLL utilizzando le tabelle del Registro di sistema senza dipendenza dallo stato corrente del sistema.  
  
- Codice di registrazione automatica è possibile negare l'accesso alle risorse di rete, ad esempio le librerie dei tipi, se il componente sia specificata come esecuzione dall'origine ed è elencato nella tabella SelfReg. Ciò può causare l'installazione del componente su errori durante un'installazione amministrativa.  
  
## <a name="see-also"></a>Vedere anche  
 [Windows Installer](/windows/desktop/Msi/windows-installer-portal)   
 [Registrazione del pacchetto gestito](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)