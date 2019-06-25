---
title: Factory dell'editor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95932b249c4ea64d14ea8ced72c1e609503ed23f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353410"
---
# <a name="editor-factories"></a>Factory dell'editor
Una factory dell'editor crea gli oggetti di editor e li inserisce in una cornice di finestra, nota come una visualizzazione fisica. Crea i dati del documento e oggetti di visualizzazione di documenti che sono necessari per creare gli editor e finestre di progettazione. Una factory dell'editor deve creare l'editor principale di Visual Studio e un editor standard. È possibile creare un editor personalizzato anche facoltativamente con una factory dell'editor.

 Si crea una factory dell'editor implementando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaccia. Nell'esempio seguente viene illustrato come implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> per creare una factory dell'editor:

 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-csharp[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]

 Un editor viene caricato la prima volta che si apre un tipo di file gestito da tale editor. È possibile scegliere di aprire un editor specifico o l'editor predefinito. Se si seleziona l'editor predefinito, l'ambiente di sviluppo integrato (IDE) determina l'editor corretto per aprire e quindi lo apre. Per altre informazioni, vedere [determinare quale editor viene aperto un file in un progetto](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md).

## <a name="register-editor-factories"></a>Registra factory dell'editor
 Prima di poter utilizzare un editor che è stato creato, è innanzitutto necessario registrare le relative informazioni, incluse le estensioni di file che possono essere gestite.

 Se il pacchetto VSPackage è scritto in codice gestito, è possibile usare il metodo di Framework di pacchetto gestito (MPF) <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> per registrare la factory dell'editor dopo il caricamento del pacchetto VSPackage. Se il pacchetto VSPackage è scritto in codice non gestito, quindi è necessario registrare la factory dell'editor tramite la <xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> servizio.

### <a name="register-an-editor-factory-by-using-managed-code"></a>Registra una factory dell'editor tramite codice gestito
 È necessario registrare la factory dell'editor in un VSPackage di `Initialize` (metodo). Chiamare innanzitutto `base.Initialize`, quindi chiamare <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> per ogni factory dell'editor

 Nel codice gestito, non è necessario annullare la registrazione di una factory dell'editor, perché il pacchetto VSPackage lo gestirà automaticamente. Inoltre, se la factory dell'editor implementa <xref:System.IDisposable>, viene eliminato automaticamente quando si è annullata la registrazione.

### <a name="register-an-editor-factory-by-using-unmanaged-code"></a>Registra una factory dell'editor tramite codice non gestito
 Nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementazione per il package editor, usare il `QueryService` metodo da chiamare `SVsRegisterEditors`. Questa operazione restituisce un puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> passando l'implementazione del metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaccia. È necessario mplementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> in una classe separata.

## <a name="the-editor-factory-registration-process"></a>Il processo di registrazione factory editor
 Il processo seguente si verifica quando Visual Studio carica l'editor utilizzando la factory dell'editor:

1. Il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] chiamate al sistema di progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.

2. Questo metodo restituisce la factory dell'editor. Ritardi di Visual Studio il caricamento del pacchetto dell'editor, tuttavia, fino a quando un sistema di progetto effettivamente necessaria per l'editor.

3. Quando l'editor è un sistema di progetto, Visual Studio chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>, un metodo specializzato che restituisce la visualizzazione del documento sia il documento di oggetti dati.

4. Se viene chiamato da Visual Studio per il factory editor con <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> restituiscono un oggetto dati del documento sia un oggetto visualizzazione del documento, Visual Studio quindi crea la finestra del documento, inserisce l'oggetto visualizzazione del documento in esso e produce una voce nel documento in esecuzione tabella (RDT) per l'oggetto dati del documento.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
- [tabella documenti in esecuzione](../extensibility/internals/running-document-table.md)