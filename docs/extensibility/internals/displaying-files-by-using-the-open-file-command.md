---
title: Visualizzazione dei file mediante il comando Apri file Documenti Microsoft
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
ms.openlocfilehash: cc18442c55b6989c4d8668e1425fdd62a2d4b1b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708602"
---
# <a name="display-files-by-using-the-open-file-command"></a>Visualizzare i file utilizzando il comando Apri file
Nei passaggi seguenti viene descritto come l'IDE gestisce il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]comando Apri **file,** disponibile nel menu **File** in . I passaggi descrivono anche come i progetti devono rispondere alle chiamate che hanno origine da questo comando.

 Quando un utente sceglie il comando **Apri file** dal menu **File** e seleziona un file dalla finestra di dialogo **Apri file,** si verifica il seguente processo:

1. Utilizzando la tabella del documento in esecuzione, l'IDE determina se il file è già aperto in un progetto.

    - Se il file è aperto, l'IDE riaffiora la finestra.

    - Se il file non è aperto, l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> per eseguire una query ogni progetto per determinare quale progetto può aprire il file.

        > [!NOTE]
        > Nell'implementazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>del progetto di , fornire un valore di priorità che indica il livello in cui il progetto apre il file. I valori di <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> priorità vengono forniti nell'enumerazione.

2. Ogni progetto risponde con un livello di priorità che indica l'importanza che attribuisce all'essere il progetto per aprire il file.

3. L'IDE utilizza i criteri seguenti per determinare quale progetto apre il file:

    - Il progetto che risponde con`DP_Intrinsic`la priorità più alta ( ) apre il file. Se più progetti rispondono con questa priorità, il primo progetto a rispondere apre il file.

    - Se nessun progetto risponde con`DP_Intrinsic`la priorità più alta ( ), ma tutti i progetti rispondono con la stessa priorità inferiore, il progetto attivo apre il file. Se non è attivo alcun progetto, il primo progetto a rispondere apre il file.

    - Se nessun progetto rivendica la`DP_Unsupported`proprietà del file ( ), il progetto File esterni apre il file.

         Se viene creata un'istanza del progetto File esterni, il progetto risponde `DP_CanAddAsExternal`sempre con il valore . Questo valore indica che il progetto può aprire il file. Questo progetto viene utilizzato per ospitare file aperti che non sono in nessun altro progetto. L'elenco di elementi in questo progetto non è persistente; questo progetto è visibile in **Esplora soluzioni** solo quando viene utilizzato per aprire un file.

         Se il progetto File esterni non indica che è possibile aprire il file, non è stata creata un'istanza del progetto. In questo caso, l'IDE crea un'istanza del progetto File esterni e indica al progetto di aprire il file.

4. Non appena l'IDE determina quale progetto apre <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> il file, chiama il metodo su tale progetto.

5. Il progetto ha quindi la possibilità di aprire il file utilizzando un editor specifico del progetto o un editor standard. Per ulteriori informazioni, vedere [Procedura: aprire gli editor specifici](../../extensibility/how-to-open-project-specific-editors.md) del progetto e Procedura: aprire rispettivamente gli editor [standard.](../../extensibility/how-to-open-standard-editors.md)

## <a name="see-also"></a>Vedere anche
- [Visualizzare i file utilizzando il comando Apri con](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)
- [Aprire e salvare elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Procedura: aprire editor specifici del progettoHow to: Open project-specific editors](../../extensibility/how-to-open-project-specific-editors.md)
- [Procedura: aprire gli editor standardHow to: Open standard editors](../../extensibility/how-to-open-standard-editors.md)
