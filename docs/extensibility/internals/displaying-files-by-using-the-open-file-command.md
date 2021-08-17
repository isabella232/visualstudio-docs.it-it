---
title: Visualizzazione di file tramite il comando Apri file | Microsoft Docs
description: Informazioni su come Visual Studio'ambiente di sviluppo integrato (IDE) gestisce il comando Apri file del menu File per visualizzare i file.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d0eef493d7a8a37a3d7c83fdaee746b59e09bfaa89cfdd7715971e4cffb3f8b9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448104"
---
# <a name="display-files-by-using-the-open-file-command"></a>Visualizzare i file usando il comando Apri file
La procedura seguente descrive come l'IDE gestisce il **comando Apri file,** disponibile nel menu **File** in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . I passaggi descrivono anche come i progetti devono rispondere alle chiamate originate da questo comando.

 Quando un utente fa clic sul comando Apri **file** dal menu **File** e seleziona un file dalla finestra di dialogo **Apri file,** si verifica il processo seguente:

1. Usando la tabella del documento in esecuzione, l'IDE determina se il file è già aperto in un progetto.

    - Se il file è aperto, l'IDE ricompare la finestra.

    - Se il file non è aperto, l'IDE chiama per eseguire query su ogni progetto per determinare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> quale progetto può aprire il file.

        > [!NOTE]
        > Nell'implementazione del progetto di specificare un valore di priorità che indica il livello <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> al quale il progetto apre il file. I valori di priorità vengono forniti <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> nell'enumerazione .

2. Ogni progetto risponde con un livello di priorità che indica l'importanza di aprire il file.

3. L'IDE usa i criteri seguenti per determinare quale progetto apre il file:

    - Il progetto che risponde con la priorità più alta ( `DP_Intrinsic` ) apre il file. Se più di un progetto risponde con questa priorità, il primo progetto che risponde apre il file.

    - Se nessun progetto risponde con la priorità più alta ( ), ma tutti i progetti rispondono con la stessa priorità inferiore, il `DP_Intrinsic` progetto attivo apre il file. Se non è attivo alcun progetto, il primo progetto che risponde apre il file.

    - Se nessun progetto dichiara la proprietà del file ( ), il progetto `DP_Unsupported` File esterni apre il file.

         Se viene creata un'istanza del progetto File esterni, il progetto risponde sempre con il valore `DP_CanAddAsExternal` . Questo valore indica che il progetto può aprire il file. Questo progetto viene usato per ospitare file aperti che non sono presenti in nessun altro progetto. L'elenco di elementi in questo progetto non è persistente. questo progetto è visibile in **Esplora soluzioni** solo quando viene usato per aprire un file.

         Se il progetto File esterni non indica che può aprire il file, non è stata creata un'istanza del progetto. In questo caso, l'IDE crea un'istanza del progetto File esterni e indica al progetto di aprire il file.

4. Non appena l'IDE determina quale progetto apre il file, chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodo su tale progetto.

5. Il progetto ha quindi la possibilità di aprire il file usando un editor specifico del progetto o un editor standard. Per altre informazioni, [vedere Procedura: Aprire editor](../../extensibility/how-to-open-project-specific-editors.md) specifici del progetto e [Procedura: Aprire editor standard](../../extensibility/how-to-open-standard-editors.md)rispettivamente.

## <a name="see-also"></a>Vedi anche
- [Visualizzare i file usando il comando Apri con](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Aprire e salvare elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Procedura: Aprire editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)
- [Procedura: Aprire editor standard](../../extensibility/how-to-open-standard-editors.md)
