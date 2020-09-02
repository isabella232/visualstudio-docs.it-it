---
title: Registrazione VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a11f05edb4e7d476fdbcab82d365f9327dd4869a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685291"
---
# <a name="vspackage-registration"></a>Registrazione di pacchetti VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

I pacchetti VSPackage devono consigliare [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] che siano installati e che debbano essere caricati. Questo processo viene eseguito scrivendo le informazioni nel registro di sistema. Si tratta di un processo tipico di un programma di installazione.  
  
> [!NOTE]
> Si tratta di una procedura accettata durante lo sviluppo di VSPackage per l'uso della registrazione automatica. Tuttavia, [!INCLUDE[vsipprvsip](../../includes/vsipprvsip-md.md)] i partner non possono spedire i propri prodotti usando la registrazione automatica come parte del programma di installazione.  
  
 Le voci del registro di sistema in un pacchetto di Windows Installer vengono in genere eseguite nella tabella del registro di sistema. È anche possibile registrare le estensioni di file nella tabella del registro di sistema. Tuttavia, Windows Installer fornisce supporto incorporato tramite le tabelle ProgId (Programmatic Identifier), Class, Extension e verb. Per altre informazioni, vedere [tabelle di database](https://msdn.microsoft.com/library/aa368259\(VS.85\).aspx).  
  
 Assicurarsi che le voci del registro di sistema siano associate al componente appropriato per la strategia side-by-side scelta. Ad esempio, le voci del registro di sistema per un file condiviso devono essere associate al componente Windows Installer del file. Analogamente, le voci del registro di sistema per un file specifico della versione devono essere associate al componente di tale file. In caso contrario, l'installazione o la disinstallazione del pacchetto VSPackage per una versione di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] potrebbe interrompere il pacchetto VSPackage in altre versioni. Per altre informazioni, vedere [supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
> Il modo più semplice per gestire la registrazione consiste nell'usare gli stessi dati negli stessi file per la registrazione degli sviluppatori e la registrazione in fase di installazione. Ad esempio, alcuni strumenti di sviluppo del programma di installazione possono utilizzare file in. reg-format in fase di compilazione. Se gli sviluppatori mantengono i file. reg per lo sviluppo e il debug quotidiani, questi stessi file possono essere inclusi automaticamente nel programma di installazione. Se non è possibile condividere automaticamente i dati di registrazione, è necessario assicurarsi che la copia del programma di installazione dei dati di registrazione sia aggiornata.  
  
## <a name="registering-unmanaged-vspackages"></a>Registrazione di pacchetti VSPackage non gestiti  
 I pacchetti VSPackage non gestiti (inclusi quelli generati dal modello di pacchetto di Visual Studio) utilizzano i file con estensione RGS di tipo ATL per archiviare le informazioni di registrazione. Il formato di file RGS è specifico di ATL e non può essere utilizzato in genere da uno strumento di creazione dell'installazione. Le informazioni di registrazione per il programma di installazione VSPackage devono essere gestite separatamente. Gli sviluppatori possono, ad esempio, memorizzare i file in formato. reg sincronizzati con le modifiche al file con estensione rgs. I file con estensione reg possono essere Uniti con RegEdit per il lavoro di sviluppo o usati da un programma di installazione.  
  
## <a name="registering-managed-vspackages"></a>Registrazione di pacchetti VSPackage gestiti  
 Lo strumento RegPkg legge gli attributi di registrazione da un pacchetto VSPackage gestito e può scrivere le informazioni direttamente nel registro di sistema o scrivere file in formato reg che possono essere usati da un programma di installazione.  
  
> [!NOTE]
> Lo strumento RegPkg non è ridistribuibile e non può essere usato per registrare un pacchetto VSPackage nel sistema di un utente.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Perché i pacchetti VSPackage non devono eseguire la registrazione automatica al momento dell'installazione  
 I programmi di installazione VSPackage non devono essere basati sulla registrazione automatica. A prima vista, mantenere i valori del registro di sistema del pacchetto VSPackage solo nel pacchetto VSPackage sembra essere una soluzione ideale. Dato che gli sviluppatori hanno bisogno dei valori del registro di sistema disponibili per il lavoro e i test di routine, è opportuno evitare di mantenere una copia separata dei dati del registro di sistema nel programma di installazione. Il programma di installazione può basarsi sul pacchetto VSPackage per scrivere i valori del registro di sistema.  
  
 In teoria, la registrazione automatica presenta diversi difetti che lo rendono non idoneo per l'installazione di VSPackage:  
  
- Per supportare correttamente l'installazione, la disinstallazione, il rollback dell'installazione e il rollback della disinstallazione, è necessario creare quattro azioni personalizzate per ogni VSPackage gestito che esegue la registrazione automatica chiamando RegPkg.  
  
- L'approccio al supporto affiancato potrebbe richiedere la creazione di quattro azioni personalizzate che richiamano RegSvr32 o RegPkg per tutte le versioni supportate di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- Non è possibile eseguire il rollback di un'installazione con moduli autoregistrati perché non esiste alcun modo per stabilire se le chiavi autoregistrate vengono usate da un'altra funzionalità o applicazione.  
  
- Le dll autoregistrate talvolta si collegano a DLL ausiliarie che non sono presenti o sono la versione errata. Al contrario, Windows Installer possibile registrare le dll utilizzando le tabelle del registro di sistema senza dipendenze dallo stato corrente del sistema.  
  
- Il codice di registrazione automatica può negare l'accesso alle risorse di rete, ad esempio le librerie dei tipi, se un componente viene specificato come Run-from-source ed è elencato nella tabella SelfReg. Questo può causare un errore di installazione del componente durante un'installazione amministrativa.  
  
## <a name="see-also"></a>Vedere anche  
 [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Registrazione del pacchetto gestito](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
