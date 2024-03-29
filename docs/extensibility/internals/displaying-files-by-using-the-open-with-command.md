---
title: Visualizzazione di file tramite il comando Apri con | Microsoft Docs
description: Informazioni su come un progetto può chiamare il comando Apri con nell'ambiente Visual Studio di sviluppo integrato (IDE) per visualizzare i file.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1930f643ee609ad101c13a7103a2c7253e7588b2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709582"
---
# <a name="display-files-by-using-the-open-with-command"></a>Visualizzare i file usando il comando Apri con
Un progetto può chiedere all'IDE di visualizzare la **finestra di dialogo** Apri con . Questa richiesta richiede all'utente di aprire un file con una selezione di editor standard. I passaggi seguenti descrivono questo processo:

1. Il progetto chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> , specificando un valore per il parametro `OSE_UseOpenWithDialog` `OSEOpenDocEditor` .

2. In base all'estensione di file del documento, l'IDE determina quali editor elencati nel Registro di sistema possono aprire il documento specificato e visualizza queste informazioni nella **finestra di** dialogo Apri con .

    > [!NOTE]
    > I progetti con un editor intrinseco  che devono essere inclusi nella finestra di dialogo Apri con devono registrare una factory dell'editor per ogni editor. Gli editor intrinseci funzionano solo insieme a un particolare tipo di progetto, che viene applicato nell'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo . L'IDE ha una factory dell'editor incorporata per l'editor di testo principale e l'editor binario. L'IDE crea anche un'istanza di una factory dell'editor per conto di ogni associazione Windows file. Un esempio di tale file è Microsoft Word.

3. Non appena l'utente seleziona un elemento dalla **finestra** di dialogo Apri con , l'IDE apre quindi il documento chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo . Per altre informazioni, [vedere Procedura: Aprire editor standard.](../../extensibility/how-to-open-standard-editors.md)

## <a name="see-also"></a>Vedi anche
- [Aprire e salvare elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Visualizzare i file usando il comando Apri file](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [Procedura: Aprire editor standard](../../extensibility/how-to-open-standard-editors.md)
