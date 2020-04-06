---
title: Registrazione di VSPackage Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a05dec8fbef40143f31f2c0ac484824717ea2e32
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703925"
---
# <a name="vspackage-registration"></a>Registrazione di pacchetti VSPackage
I pacchetti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage devono informare che sono installati e devono essere caricati. Questo processo viene eseguito scrivendo informazioni nel Registro di sistema. Questo è un tipico lavoro di un installatore.

> [!NOTE]
> È una pratica accettata durante lo sviluppo di VSPackage per utilizzare l'autoregistrazione. Tuttavia, [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] i partner non possono spedire i loro prodotti utilizzando l'autoregistrazione come parte della configurazione.

 Le voci del Registro di sistema in un pacchetto di Windows Installer vengono in genere eseguite nella tabella del Registro di sistema. È inoltre possibile registrare le estensioni dei file nella tabella del Registro di sistema. Tuttavia, Windows Installer fornisce supporto incorporato tramite l'identificatore a livello di codice (ProgId), classe, estensione e tabelle dei verbi. Per ulteriori informazioni, vedere [Tabelle di database](/windows/desktop/Msi/database-tables).

 Assicurarsi che le voci del Registro di sistema siano associate al componente appropriato per la strategia side-by-side scelta. Ad esempio, le voci del Registro di sistema per un file condiviso devono essere associate al componente Windows Installer di tale file. Analogamente, le voci del Registro di sistema per un file specifico della versione devono essere associate al componente di tale file. In caso contrario, l'installazione o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la disinstallazione del pacchetto VSPackage per una versione di potrebbe interrompere il pacchetto VSPackage in altre versioni. Per ulteriori informazioni, vedere [Supporto di più versioni di Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

> [!NOTE]
> Il modo più semplice per gestire la registrazione consiste nell'utilizzare gli stessi dati negli stessi file sia per la registrazione dello sviluppatore che per la registrazione in fase di installazione. Ad esempio, alcuni strumenti di sviluppo del programma di installazione possono utilizzare file in formato reg in fase di compilazione. Se gli sviluppatori gestiscono i file reg per lo sviluppo e il debug quotidiano, gli stessi file possono essere inclusi automaticamente nel programma di installazione. Se non è possibile condividere automaticamente i dati di registrazione, è necessario assicurarsi che la copia del programma di installazione dei dati di registrazione sia aggiornata.

## <a name="registering-unmanaged-vspackages"></a>Registrazione di VSPackage non gestitiRegistering Unmanaged VSPackages
 VSPackage non gestiti (inclusi quelli generati dal modello di pacchetto di Visual Studio) utilizzano i file RGS di tipo ATL per archiviare le informazioni di registrazione. Il formato di file RGS è specifico di ATL e in genere non può essere utilizzato così com'è da uno strumento di creazione dell'installazione. Le informazioni di registrazione per il programma di installazione VSPackage devono essere gestite separatamente. Ad esempio, gli sviluppatori possono mantenere i file in formato reg sincronizzati con le modifiche ai file RGS. I file reg possono essere uniti con RegEdit per il lavoro di sviluppo o utilizzati da un programma di installazione.

## <a name="registering-managed-vspackages"></a>Registrazione di VSPackage gestitiRegistering Managed VSPackages
 Lo strumento RegPkg legge gli attributi di registrazione da un VSPackage gestito e può scrivere le informazioni direttamente nel Registro di sistema o scrivere file in formato reg che possono essere utilizzati da un programma di installazione.

> [!NOTE]
> Lo strumento RegPkg non è ridistribuibile e non può essere utilizzato per registrare un pacchetto VSPackage nel sistema di un utente.

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Perché i pacchetti VSPackage non devono autoregistrarsi in fase di installazioneWhy VSPackages Should Not Self-Register at Install Time
 I programmi di installazione VSPackage non devono basarsi sull'autoregistrazione. A prima vista, mantenere i valori del Registro di sistema di un VSPackage solo nel pacchetto VSPackage stesso sembra una buona idea. Dato che gli sviluppatori hanno bisogno dei valori del Registro di sistema disponibili per il loro lavoro di routine e test, ha senso evitare di mantenere una copia separata dei dati del Registro di sistema nel programma di installazione. Il programma di installazione può basarsi sul pacchetto VSPackage stesso per scrivere i valori del Registro di sistema.

 Mentre buono in teoria, auto-registrazione ha diversi difetti che lo rendono inadatto per l'installazione VSPackage:

- Il supporto corretto dell'installazione, della disinstallazione, del rollback dell'installazione e della disinstallazione richiede la creazione di quattro azioni personalizzate per ogni VSPackage gestito che si autoregistra chiamando RegPkg.

- Il tuo approccio al supporto side-by-side potrebbe richiedere la creazione di quattro azioni personalizzate [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]che richiamano RegSvr32 o RegPkg per ogni versione supportata di .

- Un'installazione con moduli auto-registrati non può essere ripristinata in modo sicuro perché non è possibile indicare se le chiavi autoregistrate sono utilizzate da un'altra funzionalità o applicazione.

- Le DLL autoregistrate a volte si collegano a DLL ausiliarie che non sono presenti o sono la versione errata. Al contrario, Windows Installer può registrare le DLL utilizzando le tabelle del Registro di sistema senza alcuna dipendenza dallo stato corrente del sistema.

- Il codice di autoregistrazione può essere negato l'accesso alle risorse di rete, ad esempio le librerie dei tipi, se un componente è sia specificato come run-from-source ed è elencato nella tabella SelfReg. Ciò può causare l'installazione del componente non riuscire durante un'installazione amministrativa.

## <a name="see-also"></a>Vedere anche
- [Programma di installazione di Windows](/windows/desktop/Msi/windows-installer-portal)
- [Registrazione dei pacchetti gestiti](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
