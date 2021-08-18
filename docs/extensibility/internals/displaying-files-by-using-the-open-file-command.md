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
ms.openlocfilehash: b9ba1acd9a1a918e70bf8ac71fb6a1d9e40a2231
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050071"
---
# <a name="display-files-by-using-the-open-file-command"></a>Visualizzare i file usando il comando Apri file
I passaggi seguenti descrivono come l'IDE gestisce il comando **Apri file,** disponibile nel menu **File** in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . I passaggi descrivono anche il modo in cui i progetti devono rispondere alle chiamate che hanno origine da questo comando.

 Quando un utente fa clic sul comando **Apri file** dal menu **File** e seleziona un file dalla finestra di dialogo **Apri file,** si verifica il processo seguente:

1. Usando la tabella di documenti in esecuzione, l'IDE determina se il file è già aperto in un progetto.

    - Se il file è aperto, l'IDE riaccese la finestra.

    - Se il file non è aperto, l'IDE chiama per eseguire una query su ogni progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> per determinare quale progetto può aprire il file.

        > [!NOTE]
        > Nell'implementazione del progetto di specificare un valore di priorità che indica il livello di apertura <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> del file da parte del progetto. I valori di priorità vengono forniti <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> nell'enumerazione .

2. Ogni progetto risponde con un livello di priorità che indica l'importanza di essere il progetto per aprire il file.

3. L'IDE usa i criteri seguenti per determinare quale progetto apre il file:

    - Il progetto che risponde con la priorità più alta ( `DP_Intrinsic` ) apre il file. Se più di un progetto risponde con questa priorità, il primo progetto che risponde apre il file.

    - Se nessun progetto risponde con la priorità più alta ( ), ma tutti i progetti rispondono con la stessa priorità più bassa, il `DP_Intrinsic` progetto attivo apre il file. Se non è attivo alcun progetto, il primo progetto a rispondere apre il file.

    - Se nessun progetto dichiara la proprietà del file ( ), il progetto `DP_Unsupported` File esterni apre il file.

         Se viene creata un'istanza del progetto File esterni, il progetto risponde sempre con il valore `DP_CanAddAsExternal` . Questo valore indica che il progetto può aprire il file. Questo progetto viene usato per ospitare file aperti che non sono presenti in nessun altro progetto. L'elenco di elementi in questo progetto non è persistente. Questo progetto è visibile in **Esplora soluzioni** solo quando viene usato per aprire un file.

         Se il progetto File esterni non indica che è possibile aprire il file, non è stata creata un'istanza del progetto. In questo caso, l'IDE crea un'istanza del progetto File esterni e indica al progetto di aprire il file.

4. Non appena l'IDE determina quale progetto apre il file, chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodo su tale progetto.

5. Il progetto ha quindi la possibilità di aprire il file usando un editor specifico del progetto o un editor standard. Per altre informazioni, [vedere Procedura: Aprire editor](../../extensibility/how-to-open-project-specific-editors.md) specifici del progetto e [Procedura: Aprire rispettivamente editor standard.](../../extensibility/how-to-open-standard-editors.md)

## <a name="see-also"></a>Vedi anche
- [Visualizzare i file usando il comando Apri con](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Aprire e salvare elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Procedura: Aprire editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)
- [Procedura: Aprire editor standard](../../extensibility/how-to-open-standard-editors.md)
