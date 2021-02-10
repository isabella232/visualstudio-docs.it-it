---
title: Visualizzazione di file tramite il comando Apri con | Microsoft Docs
description: Informazioni su come un progetto può chiamare il comando Apri con in Visual Studio Integrated Development Environment (IDE) per visualizzare i file.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9426b60013ae17eec872a665666a60d1fdfc1bc8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946722"
---
# <a name="display-files-by-using-the-open-with-command"></a>Visualizzare i file tramite il comando Apri con
Un progetto può richiedere all'IDE di visualizzare la finestra di dialogo **Apri con** . Questa richiesta richiede all'utente di aprire un file con una selezione di editor standard. La procedura seguente descrive questo processo:

1. Il progetto chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> , specificando il valore `OSE_UseOpenWithDialog` per il `OSEOpenDocEditor` parametro.

2. In base all'estensione del nome di file del documento, l'IDE determina quali editor elencati nel registro di sistema possono aprire il documento specificato e visualizza queste informazioni nella finestra **di dialogo Apri con** .

    > [!NOTE]
    > I progetti che dispongono di un editor intrinseco che deve essere incluso nella finestra di dialogo **Apri con** devono registrare una factory dell'editor per ogni editor di questo tipo. Gli editor intrinseci funzionano solo insieme a un determinato tipo di progetto, che viene applicato nell'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo. L'IDE include una factory dell'editor predefinita per l'editor di testo principale e l'editor binario. L'IDE crea anche un'istanza di una factory dell'editor per conto di ogni associazione di file di Windows registrata. Un esempio di tale file è Microsoft Word.

3. Non appena l'utente seleziona un elemento dalla finestra di dialogo **Apri con** , l'IDE apre il documento chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo. Per altre informazioni, vedere [procedura: aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Vedi anche
- [Apri e Salva elementi progetto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Visualizzare i file tramite il comando Apri file](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [Procedura: aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md)
