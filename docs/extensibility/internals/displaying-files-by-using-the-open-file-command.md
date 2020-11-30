---
title: Visualizzazione di file tramite il comando Apri file | Microsoft Docs
description: Informazioni sul modo in cui Visual Studio Integrated Development Environment (IDE) gestisce il comando Apri file nel menu file per visualizzare i file.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open File command
- Open File command
- persistence, supporting Open File command
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5a932a9b56a63069e010cb2b945de25564c2d135
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328340"
---
# <a name="display-files-by-using-the-open-file-command"></a>Visualizzare i file tramite il comando Apri file
Nei passaggi seguenti viene descritto il modo in cui l'IDE gestisce il comando **Apri file** , disponibile nel menu **file** di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . I passaggi descrivono inoltre come i progetti devono rispondere alle chiamate che provengono da questo comando.

 Quando un utente fa clic sul comando **Apri file** dal menu **file** e seleziona un file nella finestra di dialogo **Apri file** , si verifica il processo seguente:

1. Utilizzando la tabella documenti in esecuzione, l'IDE determina se il file è già aperto in un progetto.

    - Se il file è aperto, l'IDE riaffiora la finestra.

    - Se il file non è aperto, l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> per eseguire una query su ogni progetto per determinare quale progetto è in grado di aprire il file.

        > [!NOTE]
        > Nell'implementazione del progetto di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> , fornire un valore di priorità che indica il livello di apertura del file da parte del progetto. I valori di priorità sono disponibili nell' <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumerazione.

2. Ogni progetto risponde con un livello di priorità che indica l'importanza per l'apertura del file da parte del progetto.

3. L'IDE usa i criteri seguenti per determinare il progetto che apre il file:

    - Il progetto che risponde con la priorità più alta ( `DP_Intrinsic` ) consente di aprire il file. Se più di un progetto risponde con questa priorità, il primo progetto da rispondere apre il file.

    - Se nessun progetto risponde con la priorità più alta ( `DP_Intrinsic` ), ma tutti i progetti rispondono con la stessa priorità più bassa, il progetto attivo apre il file. Se non è attivo alcun progetto, il primo progetto da rispondere apre il file.

    - Se nessun progetto rivendica la proprietà del file ( `DP_Unsupported` ), il progetto file esterni apre il file.

         Se viene creata un'istanza del progetto di file esterni, il progetto risponde sempre con il valore `DP_CanAddAsExternal` . Questo valore indica che il progetto può aprire il file. Questo progetto viene usato per ospitare file aperti che non si trovano in nessun altro progetto. L'elenco di elementi in questo progetto non è permanente. Questo progetto è visibile in **Esplora soluzioni** solo quando viene usato per aprire un file.

         Se il progetto di file esterni non indica che è in grado di aprire il file, non è stata creata un'istanza del progetto. In questo caso, l'IDE crea un'istanza del progetto di file esterni e indica al progetto di aprire il file.

4. Non appena l'IDE determina quale progetto apre il file, chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodo su tale progetto.

5. Il progetto ha quindi la possibilità di aprire il file usando un editor standard o un editor specifico del progetto. Per altre informazioni, vedere [procedura: aprire editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md) e [procedura: aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md)rispettivamente.

## <a name="see-also"></a>Vedi anche
- [Visualizzare i file tramite il comando Apri con](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Apri e Salva elementi progetto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Procedura: aprire editor specifici del progetto](../../extensibility/how-to-open-project-specific-editors.md)
- [Procedura: aprire gli editor standard](../../extensibility/how-to-open-standard-editors.md)
