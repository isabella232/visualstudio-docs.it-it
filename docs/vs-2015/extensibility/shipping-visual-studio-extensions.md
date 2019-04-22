---
title: Forniscono estensioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c7154395be43f6a0b07e9f2557d94fa594ef5ba4
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59647201"
---
# <a name="shipping-visual-studio-extensions"></a>Distribuzione delle estensioni di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Nota**: Raccolta di Visual Studio verrà sostituita da Visual Studio Marketplace. Vedere la versione più recente di questo argomento per informazioni dettagliate.

Dopo aver completato lo sviluppo dell'estensione, è possibile installarla in altri computer, condividerlo con i colleghi e amici o pubblicarlo nella raccolta di Visual Studio. In questa sezione viene illustrato tutto ciò è necessario eseguire per pubblicare e gestire l'estensione: uso dei file con estensione VSIX, pubblicazione, localizzazione e l'aggiornamento.

## <a name="working-with-vsix-extensions"></a>Utilizzo di estensioni VSIX
 È possibile creare un estensioni VSIX creando un progetto VSIX vuota e quindi aggiungere i modelli di elemento diverso. Per altre informazioni, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).

 È possibile utilizzare il formato VSIX per i modelli di progetto del pacchetto, componenti di modelli, i pacchetti VSPackage, Managed Extensibility Framework (MEF), di elemento **casella degli strumenti** controlli, assembly e tipi personalizzati (che include le pagine iniziali personalizzate). Il formato VSIX Usa la distribuzione basata su file. Per altre informazioni sui pacchetti VSIX, vedere [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md).

 Il formato VSIX non supporta l'installazione di frammenti di codice. Inoltre non supporta alcuni altri scenari, ad esempio la scrittura alla Global Assembly Cache (GAC) o al Registro di sistema. Se è necessario scrivere nella Global Assembly Cache o il Registro di sistema durante l'installazione, è necessario utilizzare il programma di installazione di Windows. Per altre informazioni, vedere [preparazione di estensioni per Windows Installer distribuzione](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-gallery"></a>Pubblicazione dell'estensione per Visual Studio Gallery
 È possibile distribuire l'estensione ad altri utenti semplicemente eseguendo mailing loro il file VSIX o inserire in un server. Ma è il modo migliore per ottenere il tuo codice nelle mani di molti utenti nel [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Sono disponibili agli utenti di Visual Studio tramite le estensioni di Visual Studio Gallery **estensioni e aggiornamenti**. Per altre informazioni, vedere [Ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

 Per un esempio completo che illustra come caricare un'estensione di Visual Studio Gallery, vedere [procedura dettagliata: Pubblicazione di un'estensione di Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Private Galleries
 Durante lo sviluppo di controlli, modelli e strumenti, è possibile condividerli con l'organizzazione inviando messaggi a una raccolta privata nella intranet. Per altre informazioni, vedere [Private Galleries](../extensibility/private-galleries.md) (Raccolte private).

## <a name="localizing-your-extension"></a>Localizzazione dell'estensione
 Se si prevede di rilasciare l'estensione in impostazioni locali diverse, è necessario considerare di localizzazione. Per una spiegazione tutti gli aspetti, vedere [localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>L'aggiornamento e controllo delle versioni dell'estensione
 Dopo aver pubblicato l'estensione, si giungerà quando è necessario eseguirne l'aggiornamento per volta. Per scoprire come aggiornare un'estensione che è stata pubblicata nella raccolta di Visual Studio, vedere [come: Aggiornare un'estensione](../extensibility/how-to-update-a-visual-studio-extension.md).

 È possibile impostare l'estensione per il supporto di più versioni di Visual Studio. Per altre informazioni, vedere [supporto di più versioni di Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Introduzione al modello di progetto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Viene illustrato come usare il modello di progetto VSIX per installare un modello di progetto personalizzato.|
|[Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Descrive i componenti di un pacchetto VSIX.|
|[Modello di progetto VSIX](../extensibility/vsix-project-template.md)|Vengono fornite istruzioni dettagliate su come creare un pacchetto e pubblicare un'estensione.|
|[Localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md)|Viene illustrato come fornire il testo localizzato per il processo di installazione usando file vsixlangpack.|
|[Procedura: Aggiornare un'estensione](../extensibility/how-to-update-a-visual-studio-extension.md)|Viene descritto come aggiornare un'estensione del sistema e su come distribuire un aggiornamento di un'estensione di Visual Studio esistente.|
|[Procedura: Aggiungere una dipendenza a un pacchetto VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Viene descritto come aggiungere i riferimenti ai pacchetti di distribuzione VSIX.|
|[Preparazione di estensioni per la distribuzione di Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Viene illustrato come distribuire un'estensione con Windows Installer.|
|[Firma di pacchetti VSIX](../extensibility/signing-vsix-packages.md)|Spiega come firmare pacchetti VSIX.|
|[Raccolte private](../extensibility/private-galleries.md)|Viene illustrato come creare raccolte private per le estensioni.|
|[Supporto di più versioni di Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Viene illustrato come utilizzare il supporto delle estensioni più versioni di Visual Studio.|
