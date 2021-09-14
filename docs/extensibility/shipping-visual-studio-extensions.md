---
title: Spedizione Visual Studio estensioni | Microsoft Docs
description: Informazioni su come pubblicare e gestire l'estensione Visual Studio SDK, tra cui l'uso di file con estensione vsix, la pubblicazione, la localizzazione e l'aggiornamento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a57cb6732c1b1cb5fa74381ab7c8bdf8208be08d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625974"
---
# <a name="shipping-visual-studio-extensions"></a>Distribuzione delle estensioni di Visual Studio
Dopo aver completato lo sviluppo dell'estensione, è possibile installarla in altri computer, condividerla con amici e colleghi o pubblicarla in Visual Studio Marketplace. In questa sezione vengono illustrate tutte le operazioni da eseguire per pubblicare e gestire l'estensione: uso di file con estensione vsix, pubblicazione, localizzazione e aggiornamento.

## <a name="working-with-vsix-extensions"></a>Uso delle estensioni VSIX
 È possibile creare estensioni VSIX creando un Project VSIX vuoto e quindi aggiungendo modelli di elemento diversi. Per altre informazioni, vedere [VsIX Project Template](../extensibility/vsix-project-template.md).

 È possibile usare il formato VSIX per creare pacchetti di modelli di progetto,  modelli di elemento, VSPackage, componenti di Managed Extensibility Framework (MEF), controlli della casella degli strumenti, assembly e tipi personalizzati (incluse le pagine iniziale personalizzate per Visual Studio 2017). Il formato VSIX usa la distribuzione basata su file. Per altre informazioni sui pacchetti VSIX, vedere [Anatomia di un pacchetto VSIX.](../extensibility/anatomy-of-a-vsix-package.md)

 Il formato VSIX non supporta l'installazione di frammenti di codice. Non supporta inoltre alcuni altri scenari, ad esempio la scrittura nella Global Assembly Cache (GAC) o nel Registro di sistema. Se è necessario scrivere nella GAC o nel Registro di sistema nell'installazione, è necessario usare il programma di Windows installazione. Per altre informazioni, vedere Preparing [Extensions for Windows Installer Deployment](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Pubblicazione dell'estensione in Visual Studio Marketplace
 È possibile distribuire l'estensione ad altri utenti semplicemente inviando loro tramite posta elettronica il file con estensione vsix o inserendo in un server. Ma il modo migliore per mettere il codice nelle mani di molte persone è metterlo [in Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs) Visual Studio Le estensioni del Marketplace sono disponibili per Visual Studio utenti tramite **Estensioni e aggiornamenti.** Per altre informazioni, vedere [Finding and Using Visual Studio Extensions](../ide/finding-and-using-visual-studio-extensions.md).

 Per un esempio completo che illustra come caricare un'estensione in Visual Studio Marketplace, vedere [Walkthrough: Publishing a Visual Studio Extension](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Private Galleries
 Quando si sviluppano controlli, modelli e strumenti, è possibile condividerli con l'organizzazione pubblicandoli in una raccolta privata nella intranet. Per altre informazioni, vedere [Raccolte private.](../extensibility/private-galleries.md)

## <a name="localizing-your-extension"></a>Localizzazione dell'estensione
 Se si prevede di rilasciare l'estensione in impostazioni locali diverse, è consigliabile prendere in considerazione la localizzazione. Per una spiegazione delle attività coinvolte, vedere [Localizzazione di pacchetti VSIX.](../extensibility/localizing-vsix-packages.md)

## <a name="updating-and-versioning-your-extension"></a>Aggiornamento e controllo delle versioni dell'estensione
 Dopo aver pubblicato l'estensione, verrà visualizzato un momento in cui sarà necessario aggiornarla. Per informazioni su come aggiornare un'estensione pubblicata in Visual Studio Marketplace, vedere [Procedura: Aggiornare un'estensione.](../extensibility/how-to-update-a-visual-studio-extension.md)

 È possibile impostare l'estensione per supportare più versioni di Visual Studio. Per altre informazioni, vedere [Supporto di più versioni di Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Introduzione al modello di progetto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Viene illustrato come usare il modello di progetto VSIX per installare un modello di progetto personalizzato.|
|[Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Descrive i componenti di un pacchetto VSIX.|
|[Modello di progetto VSIX](../extensibility/vsix-project-template.md)|Fornisce istruzioni dettagliate su come creare un pacchetto e pubblicare un'estensione.|
|[Localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md)|Viene illustrato come fornire testo localizzato per il processo di installazione usando i file extension.vsixlangpack.|
|[Procedura: Aggiornare un'estensione](../extensibility/how-to-update-a-visual-studio-extension.md)|Viene descritto come aggiornare un'estensione nel sistema e come distribuire un aggiornamento a un'estensione Visual Studio esistente.|
|[Procedura: Aggiungere una dipendenza a un pacchetto VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Viene descritto come aggiungere riferimenti ai pacchetti di distribuzione VSIX.|
|[Preparazione di estensioni per la distribuzione di Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Viene illustrato come distribuire l'estensione con Windows programma di installazione.|
|[Firma di pacchetti VSIX](../extensibility/signing-vsix-packages.md)|Viene illustrato come firmare pacchetti VSIX.|
|[Raccolte private](../extensibility/private-galleries.md)|Viene illustrato come creare raccolte private per le estensioni.|
|[Supporto di più versioni di Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Illustra come fare in modo che l'estensione supporti più versioni di Visual Studio.|
|[Individuazione di Visual Studio](locating-visual-studio.md)|Viene descritto come individuare le istanze Visual Studio per la distribuzione di estensioni personalizzate.|
