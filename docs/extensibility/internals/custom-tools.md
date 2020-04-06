---
title: Strumenti personalizzati - Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e60f1d8cb8b25ed50b0b20c5ebb538286687ad72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708952"
---
# <a name="custom-tools"></a>Strumenti personalizzati
*Gli strumenti personalizzati* consentono di associare uno strumento a un elemento in un progetto ed eseguire tale strumento ogni volta che il file viene salvato. Alcuni strumenti personalizzati, a volte indicati come generatori di file singolo , vengono spesso *utilizzati*per implementare convertitori che generano codice dai dati e viceversa. Ad esempio, i generatori [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] di file singolo creano e codificano i file *.settings* e *.resx.* Il codice sorgente generato fornisce un accesso fortemente tipizzato ai dati nei file *.settings* e *.resx.* I [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] tipi e di progetto supportano gli strumenti personalizzati; [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] tipi di progetto non lo fanno. I propri tipi di progetto possono anche supportare strumenti personalizzati.

 Gli strumenti personalizzati sono `IVsSingleFileGenerator` componenti registrati che implementano l'interfaccia.

 Gli strumenti personalizzati `ProjectItem` sono associati a un oggetto interfaccia e sono simili a finestre di progettazione ed editor. Uno strumento personalizzato accetta il `ProjectItem` file rappresentato da un come input `DefaultExtension` e scrive un nuovo file il cui nome viene fornito dal metodo .

## <a name="in-this-section"></a>Contenuto della sezione
- [Implementare generatori a file singolo](../../extensibility/internals/implementing-single-file-generators.md)

 Viene descritto come <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> utilizzare l'interfaccia per implementare uno strumento personalizzato.

- [Registrare generatori di file singoli](../../extensibility/internals/registering-single-file-generators.md)

 Fornisce le descrizioni per tutte le voci del Registro di sistema per uno strumento personalizzato.

- [Esporre i tipi alle finestre di progettazione visivaExpose types to visual designers](../../extensibility/internals/exposing-types-to-visual-designers.md)

 Viene illustrato come i sistemi di progetto forniscono supporto alle finestre di progettazione visiva per accedere alle classi e ai tipi generati tramite file eseguibili portabili temporanei (PE).

- [Rendere persistente la proprietà di un elemento di progettoPersist the property of a project item](../../extensibility/persisting-the-property-of-a-project-item.md)

 Viene illustrato come rendere persistente una proprietà dell'elemento di progetto, ad esempio l'autore di un file di origine, nel file di progetto.

## <a name="reference"></a>Informazioni di riferimento
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>Fornisce informazioni <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>dettagliate su , che trasforma un singolo file di input in un singolo file di output che può essere compilato o aggiunto a un progetto.

 <xref:EnvDTE.ProjectItem>Viene illustrata l'interfaccia, `ProjectItem` che rappresenta un elemento in un progetto.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>Fornisce informazioni `DefaultExtension` dettagliate sul metodo , che recupera l'estensione del nome file assegnata al nome del file di output.

## <a name="related-sections"></a>Sezioni correlate
- [Estendere i progetti](../../extensibility/extending-projects.md)

 Descrive come usare i progetti e le soluzioni di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per organizzare file di codice e file di risorse e come implementare il controllo del codice sorgente.
