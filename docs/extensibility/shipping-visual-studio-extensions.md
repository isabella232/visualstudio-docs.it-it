---
title: Distribuzione delle estensioni di Visual Studio Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 767bb24bb5cb47f1af1452aa04ebdc91c778e284
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700115"
---
# <a name="shipping-visual-studio-extensions"></a>Distribuzione delle estensioni di Visual Studio
Dopo aver completato lo sviluppo dell'estensione, è possibile installarla in altri computer, condividerla con amici e colleghi o pubblicarla in Visual Studio Marketplace. In questa sezione vengono illustrate tutte le operazioni da eseguire per pubblicare e gestire l'estensione: utilizzo di file vsix, pubblicazione, localizzazione e aggiornamento.

## <a name="working-with-vsix-extensions"></a>Utilizzo delle estensioni VSIXWorking with VSIX Extensions
 È possibile creare un'estensione VSIX creando un progetto VSIX vuoto e quindi aggiungendo diversi modelli di elemento. Per ulteriori informazioni, vedere modello di [progetto VSIX](../extensibility/vsix-project-template.md).

 È possibile usare il formato VSIX per creare pacchetti di modelli di progetto, modelli di elemento, package VS, componenti Managed Extensibility Framework (MEF), controlli **della casella degli strumenti,** assembly e tipi personalizzati (incluse le pagine iniziali personalizzate per Visual Studio 2017). Il formato VSIX utilizza la distribuzione basata su file. Per altre informazioni sui pacchetti VSIX, vedere [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md).

 Il formato VSIX non supporta l'installazione di frammenti di codice. Inoltre, non supporta alcuni altri scenari, ad esempio la scrittura nella Global Assembly Cache (GAC) o nel Registro di sistema. Se è necessario scrivere nella Global Assembly Cache o nel Registro di sistema nell'installazione, è necessario utilizzare Windows Installer. Per ulteriori informazioni, vedere [Preparazione delle estensioni per](../extensibility/preparing-extensions-for-windows-installer-deployment.md)la distribuzione di Windows Installer .

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Pubblicazione dell'estensione in Visual Studio Marketplace
 È possibile distribuire l'estensione ad altre persone semplicemente inviando loro il file VSIX o mettendo su un server. Ma il modo migliore per ottenere il codice nelle mani di un sacco di persone è quello di metterlo in [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). Le estensioni di Visual Studio Marketplace sono disponibili per gli utenti di Visual Studio tramite **estensioni e aggiornamenti**. Per ulteriori informazioni, vedere [Ricerca e utilizzo delle estensioni](../ide/finding-and-using-visual-studio-extensions.md)di Visual Studio .

 Per un esempio completo che illustra come caricare un'estensione in Visual Studio Marketplace, vedere [Procedura dettagliata: pubblicazione di un'estensione](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)di Visual Studio .

## <a name="private-galleries"></a>Private Galleries
 Quando si sviluppano controlli, modelli e strumenti, è possibile condividerli con l'organizzazione pubblicandoli in una raccolta privata nella rete Intranet. Per ulteriori informazioni, vedere [Raccolte private](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Localizzazione dell'estensione
 Se si prevede di rilasciare l'estensione in impostazioni locali diverse, è consigliabile localizzarla. Per una spiegazione di ciò che è coinvolto, vedere localizzazione di [pacchetti VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Aggiornamento e controllo delle versioni dell'estensioneUpdating and Versioning your Extension
 Dopo aver pubblicato l'estensione, verrà un momento in cui è necessario aggiornarla. Per informazioni su come aggiornare un'estensione pubblicata in Visual Studio Marketplace, vedere [Procedura: aggiornare un'estensione](../extensibility/how-to-update-a-visual-studio-extension.md).

 È possibile impostare l'estensione per supportare più versioni di Visual Studio.You can set your extension to support multiple versions of Visual Studio. Per ulteriori informazioni, vedere [Supporto di più versioni di Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Introduzione al modello di progetto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Viene illustrato come utilizzare il modello di progetto VSIX per installare un modello di progetto personalizzato.|
|[Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Descrive i componenti di un pacchetto VSIX.|
|[Modello di progetto VSIX](../extensibility/vsix-project-template.md)|Fornisce istruzioni dettagliate su come creare un pacchetto e pubblicare un'estensione.|
|[Localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md)|Viene illustrato come fornire testo localizzato per il processo di installazione utilizzando i file extension.vsixlangpack.|
|[Procedura: Aggiornare un'estensione](../extensibility/how-to-update-a-visual-studio-extension.md)|Viene descritto come aggiornare un'estensione nel sistema e come distribuire un aggiornamento a un'estensione di Visual Studio esistente.|
|[Procedura: Aggiungere una dipendenza a un pacchetto VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Viene descritto come aggiungere riferimenti ai pacchetti di distribuzione VSIX.|
|[Preparazione di estensioni per la distribuzione di Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Viene illustrato come distribuire l'estensione con Windows Installer.|
|[Firma di pacchetti VSIX](../extensibility/signing-vsix-packages.md)|Viene illustrato come firmare pacchetti VSIX.|
|[Raccolte private](../extensibility/private-galleries.md)|Viene illustrato come creare raccolte private per le estensioni.|
|[Supporto di più versioni di Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Viene illustrato come fare in modo che l'estensione supporti più versioni di Visual Studio.Shows how to have your extension support multiple versions of Visual Studio.|
|[Individuazione di Visual Studio](locating-visual-studio.md)|Viene descritto come individuare le istanze di Visual Studio per la distribuzione di estensioni personalizzate.|
