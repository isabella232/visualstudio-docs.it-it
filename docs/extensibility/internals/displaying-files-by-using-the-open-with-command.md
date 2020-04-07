---
title: Visualizzazione di file mediante il comando Apri con Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4051793077e613981e1dd5b44f1736878f5853e9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708584"
---
# <a name="display-files-by-using-the-open-with-command"></a>Visualizzare i file utilizzando il comando Apri con
Un progetto può richiedere all'IDE per visualizzare il **Apri con** la finestra di dialogo. Questa richiesta richiede all'utente di aprire un file con una selezione di editor standard. I passaggi seguenti descrivono questo processo:The following steps describe this process:

1. Il progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>chiama , specificando `OSE_UseOpenWithDialog` un `OSEOpenDocEditor` valore di per il parametro.

2. In base all'estensione del nome file del documento, l'IDE determina quali editor elencati nel Registro di sistema possono aprire il documento specificato e visualizza queste informazioni nella finestra di dialogo **Apri con** .

    > [!NOTE]
    > I progetti che dispongono di un editor intrinseco che deve essere incluso nella finestra di dialogo **Apri con** devono registrare una factory dell'editor per ogni editor di questo tipo. Gli editor intrinseci funzionano solo con un particolare tipo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> progetto, che viene applicato nell'implementazione del metodo. L'IDE dispone di una factory di editor incorporata per l'editor di testo principale e l'editor binario. L'IDE crea anche un'istanza di una factory dell'editor per conto di ogni associazione di file di Windows registrata. Un esempio di tale file è Microsoft Word.

3. Non appena l'utente seleziona un elemento dal **Apri con** finestra di dialogo, l'IDE quindi apre il documento chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> il metodo. Per ulteriori informazioni, vedere [Procedura: aprire editor standard](../../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Vedere anche
- [Aprire e salvare elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Visualizzare i file utilizzando il comando Apri file](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [Procedura: aprire gli editor standardHow to: Open standard editors](../../extensibility/how-to-open-standard-editors.md)
