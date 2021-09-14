---
title: Anatomia di un pacchetto VSIX | Microsoft Docs
description: Informazioni sul contenuto di un pacchetto VSIX in Visual Studio, un file che contiene una o più estensioni Visual Studio e un file manifesto dei metadati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9485aeba7d531c0a05f33ad759688e9fd05a29f9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709824"
---
# <a name="anatomy-of-a-vsix-package"></a>Anatomia di un pacchetto VSIX
Un pacchetto VSIX è un file *vsix* che contiene una o più estensioni Visual Studio, insieme ai metadati Visual Studio per classificare e installare le estensioni. I metadati sono contenuti nel manifesto VSIX e *nel file [Content_Types].xml.* Un pacchetto VSIX può anche contenere uno o più file *Extension.vsixlangpack* per fornire il testo di installazione localizzato e può contenere pacchetti VSIX aggiuntivi per installare le dipendenze.

 Il formato del pacchetto VSIX segue lo standard Open Packaging Conventions (OPC). Il pacchetto contiene file binari e file di supporto, insieme a un file *[Content_Types].xml* e un file *manifesto vsix.* Un pacchetto VSIX può contenere l'output di più progetti o anche di più pacchetti con manifesti propri.

> [!NOTE]
> I nomi dei file inclusi nei pacchetti VSIX non devono includere spazi, né caratteri riservati in URI (Uniform Resource Identifier), come definito in [ \[ RFC2396. \] ](https://www.rfc-editor.org/rfc/rfc2396.txt)

## <a name="the-vsix-manifest"></a>Manifesto VSIX
 Il manifesto VSIX contiene informazioni sull'estensione da installare e segue lo schema VSX. Per altre informazioni, vedere Informazioni [di riferimento sullo schema dell'estensione VSIX 1.0.](/previous-versions/dd393700(v=vs.110)) Per un esempio di manifesto VSIX, vedere [Elemento PackageManifest (elemento radice, schema VSX).](/previous-versions/dd393754(v=vs.110))

 Il manifesto VSIX deve essere `extension.vsixmanifest` denominato quando è incluso in un file ^.vsix*.

## <a name="the-content"></a>Il contenuto
 Un pacchetto VSIX può contenere modelli, elementi della casella degli strumenti, VSPackage o qualsiasi altro tipo di estensione supportato da Visual Studio.

## <a name="language-packs"></a>Language Pack
 Un pacchetto VSIX può contenere una o più *file Extension.vsixlangpack* per fornire testo localizzato durante l'installazione. Per altre informazioni, vedere [Localizzazione di pacchetti VSIX.](../extensibility/localizing-vsix-packages.md)

## <a name="dependencies-and-references"></a>Dipendenze e riferimenti
 Un pacchetto VSIX può contenere altri pacchetti VSIX come riferimenti. Ognuno di questi altri pacchetti deve includere il proprio manifesto VSIX.

 Se un utente tenta di installare un'estensione con dipendenze, il programma di installazione verifica che gli assembly necessari siano installati nel sistema utente. Se gli assembly necessari non vengono trovati, **in Estensioni** e aggiornamenti viene visualizzato un elenco degli assembly mancanti.

 Se il manifesto dell'estensione include uno o più elementi [Reference,](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) **Extensions and Updates** confronta il manifesto di ogni riferimento con le estensioni installate nel sistema e installa l'estensione a cui si fa riferimento se non è già installata. Se è installata una versione precedente di un'estensione a cui si fa riferimento, la versione più recente la sostituisce.

 Se un progetto in una soluzione con più progetti include un riferimento a un altro progetto nella stessa soluzione, il pacchetto VSIX include le dipendenze del progetto. È possibile eseguire l'override di questo comportamento selezionando il  riferimento per il progetto interno e quindi nella finestra Proprietà impostare la proprietà Gruppi di **output inclusi in VSIX** su `BuiltProjectOutputGroup` .

 Per includere dll satellite da assembly a cui si fa riferimento nel pacchetto VSIX, aggiungere alla proprietà Gruppi di `SatelliteDllsProjectOutputGroup` **output inclusi in VSIX.**

## <a name="installation-location"></a>Percorso di installazione
 Durante l'installazione, Estensioni e **aggiornamenti** cerca il contenuto del pacchetto VSIX in una cartella in *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions.*

 Per impostazione predefinita, l'installazione si applica solo all'utente corrente, perché *%LocalAppData%* è una directory specifica dell'utente. Tuttavia, se si imposta [l'elemento AllUsers](/previous-versions/ee191547(v=vs.110)) del manifesto su `True` , l'estensione verrà installata in <em>. \\ </em> VisualStudioInstallationFolder<em>\Common7\IDE\Extensions</em> e sarà disponibile per tutti gli utenti del computer.

## <a name="content_typesxml"></a>[Content_Types].xml
 Il *file [Content_Types].xml* identifica i tipi di file nel file *vsix* espanso. Visual Studio questo file viene utilizzato durante l'installazione del pacchetto, ma non viene installato il file stesso. Per altre informazioni su questo file, vedere [La struttura del file [Content_types].xml](the-structure-of-the-content-types-dot-xml-file.md).

 Un *file [Content_Types].xml* è richiesto dallo standard Open Packaging Conventions (OPC). Per altre informazioni su OPC, vedere [OPC: A new standard for packaging your data (OPC: un nuovo standard](/archive/blogs/msdnmagazine/opc-a-new-standard-for-packaging-your-data) per la creazione di pacchetti dei dati) nel sito Web MSDN.