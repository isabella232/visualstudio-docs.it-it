---
title: Anatomia di un pacchetto VSIX Documenti Microsoft
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
ms.openlocfilehash: 8a6d3f994c531bd36ab4281c5f0b27e993cd3392
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740087"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomia di un pacchetto VSIX
Un pacchetto VSIX è un file *VSIX* che contiene una o più estensioni di Visual Studio, insieme ai metadati utilizzati da Visual Studio per classificare e installare le estensioni. Tali metadati sono contenuti nel manifesto VSIX e nel file *[Content_Types].xml.* Un pacchetto VSIX può anche contenere uno o più file *Extension.vsixlangpack* per fornire testo di installazione localizzato e può contenere pacchetti VSIX aggiuntivi per installare le dipendenze.

 Il formato del pacchetto VSIX segue lo standard Open Packaging Conventions (OPC). Il pacchetto contiene file binari e file di supporto, insieme a un file *[Content_Types].xml* e un file manifesto *Con estensione vsix.* Un pacchetto VSIX può contenere l'output di più progetti o anche più pacchetti che hanno i propri manifesti.

> [!NOTE]
> I nomi dei file inclusi nei pacchetti VSIX non devono includere spazi, né caratteri riservati in URI (Uniform Resource Identifier), come definito in [ \[RFC2396\]](https://www.rfc-editor.org/rfc/rfc2396.txt).

## <a name="the-vsix-manifest"></a>Manifesto VSIX
 Il manifesto VSIX contiene informazioni sull'estensione da installare e segue lo schema VSX. Per altre informazioni, vedere riferimento allo schema di estensione VSIX 1.0.For more information, see [VSIX extension schema 1.0 reference](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Per un esempio di manifesto VSIX, vedere [elemento PackageManifest (elemento radice, schema VSX).](https://msdn.microsoft.com/library/f8ae42ba-775a-4d2b-976a-f556e147f187)

 Il manifesto VSIX `extension.vsixmanifest` deve essere denominato quando viene incluso in un file con estensione vsix.

## <a name="the-content"></a>Il contenuto
 Un pacchetto VSIX può contenere modelli, elementi della casella degli strumenti, package VS o qualsiasi altro tipo di estensione supportata da Visual Studio.A VSIX package may contain templates, toolbox items, VSPackages, or any other kind of extension that is supported by Visual Studio.

## <a name="language-packs"></a>Language Pack
 Un pacchetto VSIX può contenere una o più file *Extension.vsixlangpack* per fornire testo localizzato durante l'installazione. Per altre informazioni, vedere [Localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md).

## <a name="dependencies-and-references"></a>Dipendenze e riferimenti
 Un pacchetto VSIX può contenere altri pacchetti VSIX come riferimenti. Ognuno di questi altri pacchetti deve includere il proprio manifesto VSIX.

 Se un utente tenta di installare un'estensione con dipendenze, il programma di installazione verifica che gli assembly necessari siano installati nel sistema utente. Se gli assembly necessari non vengono trovati, **Estensioni e aggiornamenti** visualizza un elenco degli assembly mancanti.

 Se il manifesto dell'estensione include uno o più elementi [Reference,](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) **Extensions and Updates** confronta il manifesto di ogni riferimento con le estensioni installate nel sistema e installa l'estensione di riferimento se non è già installata. Se è installata una versione precedente di un'estensione di riferimento, la versione più recente la sostituisce.

 Se un progetto in una soluzione multiprogetto include un riferimento a un altro progetto nella stessa soluzione, il pacchetto VSIX include le dipendenze di tale progetto. È possibile eseguire l'override di questo comportamento facendo clic sul riferimento per il progetto interno `BuiltProjectOutputGroup`e quindi, nella finestra **Proprietà,** impostando la proprietà Gruppi di output inclusi in **VSIX** su .

 Per includere le DLL satellite dagli assembly di riferimento `SatelliteDllsProjectOutputGroup` nel pacchetto VSIX, aggiungere alla proprietà Gruppi di **output inclusi in VSIX.**

## <a name="installation-location"></a>Percorso di installazione
 Durante l'installazione, **Extensions and Updates** cerca il contenuto del pacchetto VSIX in una cartella in *%LocalAppData%*

 Per impostazione predefinita, l'installazione si applica solo all'utente corrente, poiché *%LocalAppData%* è una directory specifica dell'utente. Tuttavia, se si imposta l'elemento `True` [AllUsers](https://msdn.microsoft.com/library/ac817f50-3276-4ddb-b467-8bbb1432455b) del manifesto su , l'estensione verrà installata in <em>.. \\ </em>VisualStudioInstallationFolder<em>, Common7 , IDE , estensioni</em> e sarà disponibile per tutti gli utenti del computer.

## <a name="content_typesxml"></a>[Content_Types].xml
 Il file *[Content_Types].xml* identifica i tipi di file nel file *VSIX* espanso. Visual Studio utilizza questo file durante l'installazione del pacchetto, ma non installa il file stesso. Per ulteriori informazioni su questo file, vedere [La struttura del file [Content_types].xml](the-structure-of-the-content-types-dot-xml-file.md).

 Un file *[Content_Types].xml* è richiesto dallo standard Open Packaging Conventions (OPC). Per ulteriori informazioni su OPC, vedere OPC: A new standard for packaging your data on the MSDN Web site [(OPC: A new standard for packaging your data](https://blogs.msdn.microsoft.com/msdnmagazine/2007/08/08/opc-a-new-standard-for-packaging-your-data/) on the MSDN Web site).
