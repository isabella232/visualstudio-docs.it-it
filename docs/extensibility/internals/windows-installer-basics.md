---
title: Nozioni di base su Windows Installer - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aeea0b17a3c234bb7670642fb9ae0a442c9d60cd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703423"
---
# <a name="windows-installer-basics"></a>Nozioni di base su Windows Installer
Windows Installer installa e disinstalla applicazioni o prodotti software nel computer di un utente, eseguendo queste attività in unità denominate componenti di Windows Installer (talvolta denominati WIC o solo componenti). Un GUID identifica ogni WIC, ovvero l'unità di base di installazione e conteggio dei riferimenti per le installazioni tramite Windows Installer.

 Per la documentazione completa di Windows Installer, vedere l'argomento di Platform [SDK, Windows Installer](/previous-versions/2kt85ked(v=vs.120)).

## <a name="authoring-a-vspackage"></a>Creazione di un pacchetto VSPackageAuthoring a VSPackage
 Windows Installer utilizza pacchetti di installazione, che contengono informazioni necessarie a Windows Installer per installare, disinstallare o ripristinare un prodotto ed eseguire l'interfaccia utente di installazione. Ogni pacchetto di installazione include un file con estensione msi, che contiene un database di installazione, un flusso di informazioni di riepilogo e flussi di dati per varie parti dell'installazione. Per utilizzare il programma di installazione, è necessario creare un'installazione. Poiché il programma di installazione organizza le installazioni in base al concetto di componenti e archivia le informazioni sull'installazione in un database relazionale, il processo di creazione di un pacchetto di installazione comporta in generale i passaggi seguenti:

1. Pianificare la creazione della configurazione per supportare il controllo delle versioni e le strategie side-by-side.

2. Identificare le funzionalità da presentare agli utenti.

3. Organizzare il pacchetto VSPackage e le dipendenze in componenti.

4. Popolare il database di installazione con le informazioni.

5. Convalidare il pacchetto di installazione.

   Questa documentazione riguarda principalmente la prima e la terza fase del processo. Durante questi passaggi si organizzano le funzionalità VSPackage in WIC in modo da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]poter inquadrare la strategia di controllo delle versioni e manutenzione per tenere conto delle versioni successive di . I tre passaggi rimanenti sono descritti in dettaglio nella documentazione di Windows Installer in Platform SDK.

## <a name="key-terms"></a>Termini chiave
 Di seguito sono riportate le definizioni dei termini chiave relativi alla tecnologia Windows Installer.

 File di risorse, chiavi del Registro di sistema, collegamenti o così via che possono essere installati in un computer. Queste risorse sono raggruppate logicamente in componenti di Windows Installer.These resources are grouped logically into Windows Installer components.

 Componente di Windows Installer (WIC) Unità di base dell'installazione che rappresenta un raggruppamento logico di risorse correlate installate e disinstallate come unità. I componenti di Windows Installer sono identificati da un ID componente univoco o GUID. Inoltre, Windows Installer mantiene il conteggio dei riferimenti a livello WIC. Per la massima flessibilità di controllo delle versioni, includere non più di una risorsa primaria, ad esempio una DLL, in un determinato WIC. Si noti che dopo aver identificato e popolato un WIC, assegnargli un GUID e distribuirlo, non è possibile modificarne la composizione. Per ulteriori informazioni, vedere [Organizzazione delle applicazioni in componenti](/windows/desktop/Msi/organizing-applications-into-components).

 Pacchetto (pacchetto Redist) Unità di distribuzione costituita da un file con estensione msi e file di origine esterni a cui il file potrebbe puntare. Un pacchetto contiene tutte le informazioni necessarie a Windows Installer per eseguire l'interfaccia utente e per installare o disinstallare l'applicazione.

 File .msi Un file di archiviazione con struttura COM contenente le istruzioni e i dati necessari per installare un'applicazione. Ogni pacchetto contiene almeno un file con estensione msi. Il file con estensione msi contiene il database del programma di installazione, un flusso di informazioni di riepilogo ed eventualmente una o più trasformazioni e file di origine interni. I file da installare possono essere compressi in un archivio e archiviati in un flusso nel file con estensione msi oppure archiviati, compressi o non compressi all'esterno del file con estensione msi nel supporto di origine. Per ulteriori informazioni, vedere [Estensioni di file](/windows/desktop/Msi/windows-installer-file-extensions)di Windows Installer .

## <a name="windows-installer-rules-enforcement"></a>Applicazione delle regole di Windows Installer
 Due set di regole determinano la distribuzione delle risorse tramite i componenti dell'installazione. Un set di regole viene gestito da Windows Installer stesso, mentre è necessario applicare il secondo set come autore dell'installazione.

> [!NOTE]
> L'imposizione delle regole di Windows Installer si verifica solo se si esegue una convalida del file con estensione msi. Tuttavia, si consiglia di considerare queste regole come procedure consigliate. Per ulteriori informazioni, vedere [Convalida di un database](/windows/desktop/Msi/validating-an-installation-database) di installazione e convalida del [pacchetto](/windows/desktop/Msi/package-validation).

#### <a name="installer-enforced-rules"></a>Regole applicate dal programma di installazione

- Tutti i file in un determinato componente devono essere installati nella stessa directory. Al contrario, i file installati in cartelle separate devono appartenere a componenti separati.

- Può essere presente un solo percorso chiave per componente. Il percorso della chiave è semplicemente un file o una chiave del Registro di sistema che rappresenta l'intero componente.

#### <a name="component-provider-responsibilities"></a>Responsabilità del fornitore di componenti

- Qualsiasi due risorse che potrebbero essere spedite separatamente nelle versioni successive devono essere presenti in componenti separati. Le risorse devono essere raggruppate nello stesso componente solo quando si è certi che queste risorse non verranno mai spedite separatamente. In effetti, è consigliabile che tutte le risorse primarie (DLL, ad esempio) esistano sempre in WIC separati. Per ulteriori informazioni, vedere [Definizione dei componenti del programma di installazione](/windows/desktop/Msi/defining-installer-components).

- Nessuna risorsa con controllo delle versioni deve mai essere spedita in più di un WIC.

## <a name="see-also"></a>Vedere anche
- [Cosa succede se le regole dei componenti vengono interrotte?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)
