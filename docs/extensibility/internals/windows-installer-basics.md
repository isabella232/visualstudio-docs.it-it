---
title: Windows Nozioni di base sul programma di installazione | Microsoft Docs
description: Informazioni su Windows installer da usare per l'installazione di un vspackage, inclusa l'organizzazione delle funzionalità di VSPackage in componenti Windows Installer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 34e36e5ff7be09c12781c18e8f4d7c842a357c6e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041815"
---
# <a name="windows-installer-basics"></a>Nozioni di base su Windows Installer
Il Windows Installer installa e disinstalla applicazioni o prodotti software nel computer di un utente, eseguendo queste attività in unità denominate componenti del programma di installazione di Windows (talvolta denominate WIC o semplicemente componenti). Un GUID identifica ogni WIC, ovvero l'unità di base di installazione e il conteggio dei riferimenti per le configurazioni Windows Installer.

 Per la documentazione completa del programma di Windows, vedere l'argomento Platform SDK, [Windows Installer](/previous-versions/2kt85ked(v=vs.120)).

## <a name="authoring-a-vspackage"></a>Creazione di un pacchetto VSPackage
 Windows Il programma di installazione usa pacchetti di installazione, che contengono informazioni che Windows installer deve installare, disinstallare o ripristinare un prodotto ed eseguire l'interfaccia utente del programma di installazione. Ogni pacchetto di installazione include un file .msi, che contiene un database di installazione, un flusso di informazioni di riepilogo e flussi di dati per varie parti dell'installazione. Per usare il programma di installazione, è necessario creare un'installazione. Poiché il programma di installazione organizza le installazioni in base al concetto di componenti e archivia le informazioni sull'installazione in un database relazionale, il processo di creazione di un pacchetto di installazione comporta in generale i passaggi seguenti:

1. Pianificare la creazione dell'installazione per supportare il controllo delle versioni e le strategie side-by-side.

2. Identificare le funzionalità da presentare agli utenti.

3. Organizzare il pacchetto VSPackage e le dipendenze in componenti.

4. Popolare il database di installazione con informazioni.

5. Convalidare il pacchetto di installazione.

   Questa documentazione riguarda principalmente il primo e il terzo passaggio del processo. Durante questi passaggi si organizzano le funzionalità vspackage in WIC in modo da poter incorniciare la strategia di controllo delle versioni e manutenzione per conto delle versioni successive di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . I tre passaggi rimanenti sono descritti in dettaglio nella Windows del programma di installazione in Platform SDK.

## <a name="key-terms"></a>Termini chiave
 Di seguito sono riportate le definizioni dei termini chiave correlati alla tecnologia Windows Installer.

 File di risorse, chiavi del Registro di sistema, collegamenti o così via che possono essere installati in un computer. Queste risorse vengono raggruppate in modo logico in componenti Windows installer.

 Windows Componente del programma di installazione (WIC) Unità di base di installazione che rappresenta un raggruppamento logico di risorse correlate installate e disinstallate come unità. Windows I componenti del programma di installazione sono identificati da un ID componente univoco o da un GUID. Inoltre, Windows installer mantiene il conteggio dei riferimenti a livello di WIC. Per la massima flessibilità di controllo delle versioni, includere non più di una risorsa primaria, ad esempio una DLL, in un wic specificato. Si noti che dopo aver identificato e popolato un WIC, assegnato un GUID e averlo distribuito, non è possibile modificarne la composizione. Per altre informazioni, vedere [Organizzazione di applicazioni in componenti](/windows/desktop/Msi/organizing-applications-into-components).

 Pacchetto (pacchetto redist) Unità di distribuzione costituita da un file .msi e da file di origine esterni a cui potrebbe puntare questo file. Un pacchetto contiene tutte le informazioni necessarie Windows installer per eseguire l'interfaccia utente e installare o disinstallare l'applicazione.

 .msi file di archiviazione con struttura COM contenente le istruzioni e i dati necessari per installare un'applicazione. Ogni pacchetto contiene almeno un .msi file. Il .msi file contiene il database del programma di installazione, un flusso di informazioni di riepilogo ed eventualmente una o più trasformazioni e file di origine interni. I file da installare possono essere compressi in un file cab e archiviati in un flusso nel file .msi o archiviati, compressi o non compressi, all'esterno del file .msi nel supporto di origine. Per altre informazioni, vedere Estensioni di [Windows installer](/windows/desktop/Msi/windows-installer-file-extensions).

## <a name="windows-installer-rules-enforcement"></a>Windows Applicazione delle regole del programma di installazione
 Due set di regole determinano la distribuzione delle risorse tramite i componenti dell'installazione. Un set di regole viene gestito dal programma di installazione Windows, mentre è necessario applicare il secondo set come autore dell'installazione.

> [!NOTE]
> L'imposizione Windows regole del programma di installazione si verifica solo se si esegue una convalida del file .msi file. Tuttavia, è consigliabile considerare queste regole come procedure consigliate. Per altre informazioni, vedere [Convalida di un database di installazione e](/windows/desktop/Msi/validating-an-installation-database) Convalida dei [pacchetti](/windows/desktop/Msi/package-validation).

#### <a name="installer-enforced-rules"></a>Installer-Enforced regole

- Tutti i file in un determinato componente devono essere installati nella stessa directory. Al contrario, i file installati in cartelle separate devono appartenere a componenti separati.

- Può essere presente un solo percorso chiave per componente. Il percorso della chiave è semplicemente un file o una chiave del Registro di sistema che rappresenta l'intero componente.

#### <a name="component-provider-responsibilities"></a>Component-Provider responsabilità

- Le due risorse che potrebbero essere disponibili separatamente nelle versioni successive devono essere presenti in componenti separati. Le risorse devono essere raggruppate nello stesso componente solo quando si è certi che queste risorse non verranno mai spedite separatamente. In realtà, è consigliabile che tutte le risorse primarie (ad esempio, le DLL) esistano sempre in WIC separate. Per altre informazioni, vedere [Definizione dei componenti del programma di installazione](/windows/desktop/Msi/defining-installer-components).

- Nessuna risorsa con controllo delle versioni deve mai essere disponibile in più di un wic.

## <a name="see-also"></a>Vedi anche
- [Cosa accade se le regole dei componenti vengono interrotte?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)
