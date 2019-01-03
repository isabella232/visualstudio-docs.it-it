---
title: Nozioni di base di Windows Installer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9eff9cb08c07c33ff2af707501f1ee6fac2e01da
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914744"
---
# <a name="windows-installer-basics"></a>Nozioni di base su Windows Installer
Il programma di installazione di Windows installa e Disinstalla applicazioni o i prodotti software nel computer dell'utente, eseguire queste attività in unità denominate i componenti di Windows Installer (denominati talvolta WICs o solo i componenti). Un GUID identifica ogni WIC, ovvero l'unità di base di conteggio dei riferimenti per le configurazioni usando Windows Installer e installazione.  
  
 Per una documentazione completa del programma di installazione di Windows, vedere l'argomento Platform SDK [Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx).  
  
## <a name="authoring-a-vspackage"></a>Creazione di un pacchetto VSPackage  
 Programma di installazione di Windows Usa pacchetti di installazione, che contengono informazioni necessarie dal programma di installazione di Windows per installare, disinstallare o ripristinare un prodotto ed eseguire l'interfaccia utente (UI) di configurazione. Ogni pacchetto di installazione include un file con estensione msi, che contiene un database di installazione, un flusso di informazioni di riepilogo e i flussi di dati di varie parti dell'installazione. Per usare il programma di installazione, è necessario creare un'installazione. Poiché il programma di installazione consente di organizzare le installazioni sul concetto di componenti e archivia le informazioni relative all'installazione in un database relazionale, il processo di creazione di un pacchetto di installazione su vasta scala comporta i passaggi seguenti:  
  
1. Pianificare l'installazione di authoring per supportare il controllo delle versioni e le strategie side-by-side.  
  
2. Identificare le funzionalità da presentare agli utenti.  
  
3. Organizzare i VSPackage e le dipendenze in componenti.  
  
4. Popolare il database di installazione con le informazioni.  
  
5. Convalidare il pacchetto di installazione.  
  
   Questa documentazione riguarda principalmente il primo e il terzo passaggio del processo. Durante questa procedura organizzare le funzionalità dei pacchetti VSPackage in WICs può definire il controllo delle versioni e strategia per le versioni successive del motivo di manutenzione [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. I rimanenti tre passaggi sono descritti dettagliatamente nella documentazione di Windows Installer in Platform SDK.  
  
## <a name="key-terms"></a>Termini chiave  
 Di seguito sono le definizioni dei termini chiave correlati alla tecnologia Windows Installer.  
  
 Risorsa  
 I file, chiavi del Registro di sistema, collegamenti, o e così via che può essere installato in un computer. Queste risorse sono raggruppate logicamente in componenti di Windows Installer.  
  
 Componente di Windows Installer (WIC)  
 L'unità di installazione che rappresenta un raggruppamento logico di risorse correlate in cui sono installati e disinstallati come un'unità di base. Componenti di Windows Installer sono identificati da un ID di componenti univoci, o GUID. Inoltre, Windows Installer mantiene il riferimento a livello di WIC di conteggio. Per una flessibilità, controllo delle versioni massimo includono non più di una risorsa primaria, ad esempio una DLL, in un determinato WIC. Si noti che dopo individuare e popolare un WIC, assegnargli un GUID e distribuirla, è possibile modificarne la composizione. Per altre informazioni, vedere [organizzare le applicazioni in componenti](/windows/desktop/Msi/organizing-applications-into-components).  
  
 Pacchetto (pacchetto Redist)  
 Un'unità di distribuzione che è costituito da un file con estensione msi e i file di origine esterna a cui questo file potrebbe fare riferimento. Un pacchetto contiene tutte le informazioni necessarie per eseguire l'interfaccia utente e per installare o disinstallare l'applicazione Windows Installer.  
  
 file con estensione msi  
 Un file di archiviazione strutturata COM che contiene le istruzioni e i dati necessari per installare un'applicazione. Ogni pacchetto contiene almeno un file con estensione msi. Il file con estensione msi contiene il database di programma di installazione, un flusso di informazioni di riepilogo e possibilmente uno o più trasformazioni e i file di origine interna. Installazione dei file possono essere compressi in un file CAB e archiviati in un flusso di file con estensione msi o archiviati, compressi o non compressi, all'esterno del file con estensione msi sul supporto di origine. Per altre informazioni, vedere [estensioni di File Windows Installer](/windows/desktop/Msi/windows-installer-file-extensions).  
  
## <a name="windows-installer-rules-enforcement"></a>Imposizione delle regole di Windows Installer  
 Due set di regole determinano la distribuzione di risorse tramite i componenti del programma di installazione. Un set di regole viene mantenuto dal programma di installazione di Windows, anche se è necessario applicare il secondo set come autore di installazione.  
  
> [!NOTE]
>  Imposizione di regole di Windows Installer si verifica solo se si esegue una convalida del file con estensione msi. Tuttavia, vengono avvisati trattare queste regole come procedure consigliate. Per altre informazioni, vedere [la convalida di un Database di installazione](/windows/desktop/Msi/validating-an-installation-database) e [convalida dei pacchetti](/windows/desktop/Msi/package-validation).  
  
#### <a name="installer-enforced-rules"></a>Regole applicate a livello di programma di installazione  
  
-   Tutti i file in un dato componente devono essere installati nella stessa directory. Al contrario, i file di installazione per separare le cartelle devono appartenere per separare i componenti.  
  
-   Può essere presente solo un percorso della chiave per ogni componente. Il percorso della chiave è semplicemente una chiave del Registro di sistema o file che rappresenta l'intero componente.  
  
#### <a name="component-provider-responsibilities"></a>Responsabilità del Provider di componenti  
  
-   Le due risorse che potrebbe essere fornito separatamente nelle versioni successive devono essere presenti in componenti separati. Le risorse devono essere raggruppate nel componente stesso, solo quando si è certi che queste risorse non verranno fornita separatamente. In effetti, è consigliabile che tutte le risorse primarie (ad esempio, DLL) esistono sempre in WICs separato. Per altre informazioni, vedere [definizione di programma di installazione di componenti](/windows/desktop/Msi/defining-installer-components).  
  
-   Alcuna risorsa con controllo delle versioni non deve sempre fornito con più WIC.  
  
## <a name="see-also"></a>Vedere anche  
 [Cosa accade se le regole dei componenti vengono interrotte.](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)