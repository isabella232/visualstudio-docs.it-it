---
title: Anatomia di un pacchetto VSIX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c52f87426b9f06ad40d77c2cc9e7be1627d2c82d
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250829"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomia di un pacchetto VSIX
Un pacchetto VSIX è un file con estensione *VSIX* che contiene una o più estensioni di Visual Studio, insieme ai metadati usati da Visual Studio per classificare e installare le estensioni. I metadati sono contenuti nel manifesto VSIX e nel file *[Content_Types]. XML* . Un pacchetto VSIX può anche contenere uno o più file con *estensione vsixlangpack* per fornire il testo di installazione localizzato e può contenere pacchetti VSIX aggiuntivi per installare le dipendenze.

 Il formato del pacchetto VSIX segue lo standard OPC (Open Packaging Conventions). Il pacchetto contiene i file binari e i file di supporto, insieme a un file di *[Content_Types]. XML* e a un file manifesto con *estensione VSIX* . Un pacchetto VSIX può contenere l'output di più progetti o anche più pacchetti con manifesti propri.

> [!NOTE]
> I nomi dei file inclusi nei pacchetti VSIX non devono includere spazi, né caratteri riservati in Uniform Resource Identifier (URI), come definito in [ \[ rfc2396 \] ](https://www.rfc-editor.org/rfc/rfc2396.txt).

## <a name="the-vsix-manifest"></a>Manifesto VSIX
 Il manifesto VSIX contiene informazioni sull'estensione da installare e segue lo schema VSX. Per altre informazioni, vedere [riferimento allo schema di estensione VSIX 1,0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Per un esempio di manifesto VSIX, vedere [elemento PackageManifest (elemento radice, schema VSX)](https://msdn.microsoft.com/library/f8ae42ba-775a-4d2b-976a-f556e147f187).

 Il manifesto VSIX deve essere denominato `extension.vsixmanifest` quando è incluso in un file ^. vsix *.

## <a name="the-content"></a>Il contenuto
 Un pacchetto VSIX può contenere modelli, elementi della casella degli strumenti, pacchetti VSPackage o qualsiasi altro tipo di estensione supportato da Visual Studio.

## <a name="language-packs"></a>Language Pack
 Un pacchetto VSIX può contenere una o più file con *estensione vsixlangpack* per fornire il testo localizzato durante l'installazione. Per ulteriori informazioni, vedere la pagina relativa alla [localizzazione dei pacchetti VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="dependencies-and-references"></a>Dipendenze e riferimenti
 Un pacchetto VSIX può contenere altri pacchetti VSIX come riferimenti. Ognuno di questi altri pacchetti deve includere il proprio manifesto VSIX.

 Se un utente tenta di installare un'estensione con dipendenze, il programma di installazione verifica che gli assembly necessari siano installati nel sistema utente. Se gli assembly richiesti non vengono trovati, **Extensions e Updates** Visualizza un elenco degli assembly mancanti.

 Se il manifesto dell'estensione include uno o più elementi di [riferimento](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) , le **estensioni e gli aggiornamenti** confrontano il manifesto di ogni riferimento alle estensioni installate nel sistema e installano l'estensione a cui si fa riferimento, se non è già installato. Se è installata una versione precedente di un'estensione a cui si fa riferimento, la versione più recente lo sostituisce.

 Se un progetto in una soluzione multiprogetto include un riferimento a un altro progetto nella stessa soluzione, il pacchetto VSIX include le dipendenze del progetto. È possibile eseguire l'override di questo comportamento selezionando il riferimento per il progetto interno e quindi, nella finestra **Proprietà** , impostando i **gruppi di output inclusi nella proprietà VSIX** su `BuiltProjectOutputGroup` .

 Per includere dll satellite da assembly a cui si fa riferimento nel pacchetto VSIX, aggiungere `SatelliteDllsProjectOutputGroup` ai **gruppi di output inclusi nella proprietà VSIX** .

## <a name="installation-location"></a>Percorso di installazione
 Durante l'installazione, le **estensioni e gli aggiornamenti** cercano il contenuto del pacchetto VSIX in una cartella in *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions*.

 Per impostazione predefinita, l'installazione viene applicata solo all'utente corrente, perché *% LocalAppData%* è una directory specifica dell'utente. Tuttavia, se si imposta l'elemento [ALLUSERS](https://msdn.microsoft.com/library/ac817f50-3276-4ddb-b467-8bbb1432455b) del manifesto su `True` , l'estensione verrà installata in <em>. \\ </em> VisualStudioInstallationFolder<em>\Common7\IDE\Extensions</em> e sarà disponibile per tutti gli utenti del computer.

## <a name="content_typesxml"></a>[Content_Types]. XML
 Il file *[Content_Types]. XML* identifica i tipi di file nel file con *estensione VSIX* espanso. Visual Studio usa questo file durante l'installazione del pacchetto, ma non installa il file stesso. Per ulteriori informazioni su questo file, vedere [la struttura del file [Content_Types]. XML](the-structure-of-the-content-types-dot-xml-file.md).

 Un file *[Content_Types]. XML* è richiesto dallo standard Open Packaging Conventions (OPC). Per ulteriori informazioni su OPC, vedere [OPC: un nuovo standard per](https://blogs.msdn.microsoft.com/msdnmagazine/2007/08/08/opc-a-new-standard-for-packaging-your-data/) la creazione di pacchetti di dati nel sito Web MSDN.
