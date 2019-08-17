---
title: Compilazione di soluzioni Office
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- debugging [Office development in Visual Studio]
- debugging Office applications in Visual Studio
- solutions [Office development in Visual Studio], debugging
- Office applications [Office development in Visual Studio], debugging
- application development [Office development in Visual Studio], building
- Office applications [Office development in Visual Studio], building
- projects [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], building
- solutions [Office development in Visual Studio], building
- Office projects [Office development in Visual Studio], debugging
- projects [Office development in Visual Studio], building
- builds [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], building
- application development [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3f89e20b710584c678c035f4d85034e90bb11323
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551850"
---
# <a name="build-office-solutions"></a>Compilazione di soluzioni Office
  I processi di compilazione e debug dei progetti di Office sono in genere analoghi agli stessi processi per altri tipi di progetti in Visual Studio, ad esempio per Windows Form. Gli argomenti di questa sezione illustrano le differenze esistenti. Per informazioni generali su come compilare applicazioni, vedere [compilazione e compilazione in Visual Studio](../ide/compiling-and-building-in-visual-studio.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="project-output-for-office-projects"></a>Output del progetto per i progetti di Office
 Il percorso di output per i progetti di Office è *nomeprogetto*\bin\release o *nomeprogetto*\bin\debug. Non è possibile eseguire la compilazione in una directory di distribuzione.

### <a name="document-level-projects"></a>Progetti a livello di documento
 Quando si compila un progetto a livello di documento, nell'output del progetto vengono inclusi gli elementi seguenti:

- Una copia del documento del progetto.

- L'assembly del progetto e tutti gli assembly di riferimento la cui proprietà **Copia localmente** è impostata su **true**.

- Il manifesto dell'applicazione, che ha l'estensione del nome file *. manifest*. Per altre informazioni, vedere [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

- Il manifesto della distribuzione, che ha l'estensione del nome file *. VSTO*. Per ulteriori informazioni, vedere [la pagina relativa ai manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md).

- Un file di database di programma (*PDB*).

> [!NOTE]
> Se si compila una soluzione a livello di documento in un percorso remoto anziché nel computer locale, aggiungere il percorso completo all'elenco di percorsi attendibili nel Centro protezione dell'applicazione. Per ulteriori informazioni, vedere la sezione concessione dell'attendibilità ai documenti in [soluzioni Office protette](../vsto/securing-office-solutions.md).

### <a name="application-level-projects"></a>Progetti a livello di applicazione
 Quando si compila un progetto di componente aggiuntivo VSTO, nell'output del progetto vengono inclusi gli elementi seguenti:

- L'assembly del progetto e tutti gli assembly di riferimento la cui proprietà **Copia localmente** è impostata su **true**.

- Il manifesto dell'applicazione, che ha l'estensione del nome file *. manifest*. Per altre informazioni, vedere [manifesti dell'applicazione per le soluzioni Office](../vsto/application-manifests-for-office-solutions.md).

- Il manifesto della distribuzione, che ha l'estensione del nome file *. VSTO*. Per ulteriori informazioni, vedere [la pagina relativa ai manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md).

- Un file di database di programma (*PDB*) per l'assembly del progetto.

  Il processo di compilazione per i progetti di componente aggiuntivo VSTO crea inoltre un set di voci del Registro di sistema nel computer di sviluppo, necessario per il caricamento del componente aggiuntivo VSTO. Per altre informazioni, vedere [voci del registro di sistema per i componenti aggiuntivi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

  Se si compila un progetto di componente aggiuntivo VSTO per Outlook che contiene aree del modulo, il processo di generazione aggiunge al Registro di sistema le informazioni aggiuntive seguenti:

- Una chiave per ogni classe di messaggi associata a una o più aree del modulo.

- Una voce per ogni area del modulo e un valore associato che rappresenta il nome del componente aggiuntivo VSTO di Outlook.

  Outlook necessita di queste informazioni per caricare le aree del modulo.

## <a name="referenced-assemblies"></a>Assembly a cui viene fatto riferimento
 È possibile fare riferimento agli assembly (compresi i progetti Libreria di classi) dal progetto Compilazione di soluzioni Office. Ogni assembly di riferimento ha una proprietà chiamata **Copia localmente**. **Copia localmente** indica se l'assembly viene copiato o meno nella directory di output. Per impostazione predefinita, questa proprietà è impostata su **true**. Ogni assembly di riferimento con la proprietà **Copia localmente** impostata su **true** viene copiato nella directory di output.

## <a name="security-during-the-build-process"></a>Sicurezza durante il processo di compilazione
 Visual Studio configura automaticamente le impostazioni di sicurezza nel computer di sviluppo per concedere l'attendibilità alla soluzione durante il processo di compilazione. Ciò consente alla soluzione di essere eseguita mentre se ne esegue il debug.

 I progetti di Office usano i certificati per verificare il server di pubblicazione. Visual Studio crea automaticamente un certificato temporaneo per identificare le soluzioni Office e configura il computer di sviluppo in modo da considerare attendibile il certificato temporaneo.

 Per altre informazioni, vedere [proteggere le soluzioni Office](../vsto/securing-office-solutions.md).

### <a name="network-projects"></a>Progetti di rete
 Se il percorso dell'assembly o del documento si trova in una condivisione di rete, l'aggiornamento dei criteri di sicurezza locali (livello utente) non è sufficiente per consentire l'esecuzione della soluzione. Un amministratore dovrà infatti concedere agli assembly e ai documenti in una condivisione di rete l'attendibilità totale a livello di computer prima che la soluzione possa essere eseguita. Per altre informazioni su come impostare i criteri di sicurezza, vedere [proteggere le soluzioni Office](../vsto/securing-office-solutions.md).

 Per i progetti a livello di documento, è necessario aggiungere anche il percorso completo del documento all'elenco delle cartelle attendibili di Office. Per ulteriori informazioni, vedere [Grant trust to Documents](../vsto/granting-trust-to-documents.md).

## <a name="change-the-platform-target"></a>Modificare la destinazione della piattaforma
 Per impostazione predefinita, la piattaforma di destinazione per i progetti di Office è **Qualsiasi CPU**. In genere, non è consigliabile modificare questa impostazione. Le soluzioni Office compilate con l'impostazione della destinazione della piattaforma impostata su **Qualsiasi CPU** vengono eseguite nelle versioni a 32 bit e a 64 bit di Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] o [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].

 È consigliabile impostare la destinazione della piattaforma su x64 solo se si crea una soluzione che verrà eseguita esclusivamente nelle versioni a 64 bit di Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] o [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]e se la soluzione chiama API native a 64 bit. Per ulteriori informazioni sulla modifica dell'impostazione di destinazione della piattaforma [, vedere Procedura: Configurare i progetti per le](../ide/how-to-configure-projects-to-target-platforms.md)piattaforme di destinazione.

 Se si imposta la destinazione della piattaforma su x64, la soluzione non verrà eseguita nelle versioni a 32 bit di Windows o di Office. Per la destinazione della piattaforma x64 è necessario che la soluzione venga eseguita in un processo a 64 bit.

## <a name="use-the-clean-command"></a>Usare il comando Pulisci
 Per rimuovere dal computer di sviluppo i file di progetto compilati, è possibile usare il comando **Pulisci** dal menu **Compilazione** di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Il comando **Pulisci** elimina tutti i file presenti nel percorso di output di compilazione. Per i progetti a livello di applicazione il comando **Pulisci** consente inoltre di rimuovere le voci del Registro di sistema create dal processo di compilazione.

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Debug di progetti di Office](../vsto/debugging-office-projects.md)|Descrive i problemi relativi al debug dei progetti di Office.|
|[Procedura dettagliata: Creazione della prima personalizzazione a livello di documento per Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Illustra come creare una personalizzazione di base a livello di documento per Excel.|
|[Procedura: Abilitare di nuovo un componente aggiuntivo VSTO disabilitato](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|Viene descritto come riabilitare un componente aggiuntivo VSTO che è stato disabilitato a livello hardware o soft.|
|[Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)|Fornisce i collegamenti a informazioni sulla creazione di soluzioni Office e sul ruolo degli assembly all'interno della soluzione.|