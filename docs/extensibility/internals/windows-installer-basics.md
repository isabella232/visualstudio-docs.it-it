---
title: Nozioni di base Windows Installer | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703423"
---
# <a name="windows-installer-basics"></a>Nozioni di base su Windows Installer
Il Windows Installer installa e Disinstalla le applicazioni o i prodotti software sul computer di un utente, eseguendo queste attività in unità denominate Windows Installer componenti (talvolta denominati WICs o solo componenti). Un GUID identifica ogni WIC, ovvero l'unità di base dell'installazione e il conteggio dei riferimenti per le configurazioni che utilizzano Windows Installer.

 Per la documentazione completa del Windows Installer, vedere l'argomento Platform SDK [Windows Installer](/previous-versions/2kt85ked(v=vs.120)).

## <a name="authoring-a-vspackage"></a>Creazione di un pacchetto VSPackage
 Windows Installer utilizza i pacchetti di installazione che contengono informazioni che Windows Installer necessario installare, disinstallare o ripristinare un prodotto ed eseguire l'interfaccia utente del programma di installazione. Ogni pacchetto di installazione include un file con estensione msi, che contiene un database di installazione, un flusso di informazioni di riepilogo e flussi di dati per varie parti dell'installazione. Per utilizzare il programma di installazione, è necessario creare un'installazione. Poiché il programma di installazione organizza le installazioni intorno al concetto di componenti e archivia le informazioni relative all'installazione in un database relazionale, il processo di creazione di un pacchetto di installazione comporta l'ampia gamma dei passaggi seguenti:

1. Pianificare la creazione dell'installazione per supportare il controllo delle versioni e le strategie side-by-side.

2. Identificare le funzionalità da presentare agli utenti.

3. Organizzare il pacchetto VSPackage e le dipendenze in componenti.

4. Inserire le informazioni nel database di installazione.

5. Convalidare il pacchetto di installazione.

   Questa documentazione riguarda principalmente il primo e il terzo passaggio del processo. Durante questi passaggi si organizzano le funzionalità VSPackage in WICs in modo da poter eseguire il frame della strategia di controllo delle versioni e di manutenzione per tenere conto delle versioni successive di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . I tre passaggi rimanenti sono descritti in dettaglio in Windows Installer documentazione in Platform SDK.

## <a name="key-terms"></a>Termini chiave
 Di seguito sono riportate le definizioni dei termini chiave relativi alla tecnologia Windows Installer.

 File di risorse, chiavi del registro di sistema, collegamenti o e così via che possono essere installati in un computer. Queste risorse sono raggruppate logicamente in componenti Windows Installer.

 Componente Windows Installer (WIC) l'unità di base dell'installazione che rappresenta un raggruppamento logico di risorse correlate installate e disinstallate come unità. Windows Installer componenti sono identificati da un ID componente univoco o GUID. Inoltre, Windows Installer gestisce il conteggio dei riferimenti a livello di WIC. Per la massima flessibilità di controllo delle versioni, includere non più di una risorsa primaria, ad esempio una DLL, in un determinato oggetto WIC. Si noti che dopo aver identificato e popolato un oggetto WIC, avere un GUID e distribuirlo, non è possibile modificarne la composizione. Per altre informazioni, vedere [organizzazione di applicazioni in componenti](/windows/desktop/Msi/organizing-applications-into-components).

 Pacchetto (pacchetto Redist) unità di distribuzione costituita da un file con estensione msi e da file di origine esterni a cui il file potrebbe puntare. Un pacchetto contiene tutte le informazioni che Windows Installer necessario eseguire l'interfaccia utente e per installare o disinstallare l'applicazione.

 File con estensione msi un file di archiviazione strutturata COM contenente le istruzioni e i dati necessari per l'installazione di un'applicazione. Ogni pacchetto contiene almeno un file con estensione msi. Il file con estensione msi contiene il database del programma di installazione, un flusso di informazioni di riepilogo e possibilmente una o più trasformazioni e file di origine interni. I file da installare possono essere compressi in un file CAB e archiviati in un flusso nel file con estensione msi o archiviati, compressi o decompressi, all'esterno del file con estensione msi sul supporto di origine. Per ulteriori informazioni, vedere [Windows Installer estensioni di file](/windows/desktop/Msi/windows-installer-file-extensions).

## <a name="windows-installer-rules-enforcement"></a>Imposizione di regole Windows Installer
 Due set di regole determinano la distribuzione delle risorse tramite i componenti dell'installazione. Un set di regole viene gestito dal Windows Installer stesso, mentre è necessario applicare il secondo set come autore dell'installazione.

> [!NOTE]
> L'imposizione delle regole di Windows Installer si verifica solo se si esegue una convalida del file con estensione msi. Tuttavia, si consiglia di considerare queste regole come procedure consigliate. Per ulteriori informazioni, vedere [convalida di un database di installazione](/windows/desktop/Msi/validating-an-installation-database) e [convalida del pacchetto](/windows/desktop/Msi/package-validation).

#### <a name="installer-enforced-rules"></a>Regole applicate dal programma di installazione

- Tutti i file in un determinato componente devono essere installati nella stessa directory. Viceversa, i file installati in cartelle separate devono appartenere a componenti distinti.

- Può essere presente un solo percorso della chiave per ogni componente. Il percorso della chiave è semplicemente un file o una chiave del registro di sistema che rappresenta l'intero componente.

#### <a name="component-provider-responsibilities"></a>Responsabilità del provider di componenti

- Due risorse che potrebbero essere fornite separatamente nelle versioni successive dovrebbero esistere in componenti distinti. Le risorse devono essere raggruppate nello stesso componente solo quando si è certi che queste risorse non verranno mai fornite separatamente. In realtà, è consigliabile che tutte le risorse primarie (ad esempio, dll) esistano sempre in WICs separate. Per ulteriori informazioni, vedere [definizione dei componenti del programma di installazione](/windows/desktop/Msi/defining-installer-components).

- Nessuna risorsa con versione deve essere distribuita in più di un WIC.

## <a name="see-also"></a>Vedere anche
- [Cosa accade se le regole dei componenti sono interrotte?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)
