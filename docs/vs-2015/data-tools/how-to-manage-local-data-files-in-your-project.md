---
title: 'Procedura: gestire file di dati locali nel progetto | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.data.LocalConnectionConverter
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- mdf files
- local data
- .mdb files
- .mdf files
- data [Visual Studio], local
- mdb files
ms.assetid: 3ffa1aa9-17e4-422c-a02f-09224828cdfc
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: b63a90a354935300c705c0bf96ae307e0468b4f9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528419"
---
# <a name="how-to-manage-local-data-files-in-your-project"></a>Procedura: gestire file di dati locali nel progetto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un file di database locale può essere incluso in un file in un progetto. La prima volta che connette a un file di database locale, è possibile scegliere di creare una copia nel progetto o connettersi a file esistente nella posizione corrente. Se ci si connette al file esistente, rimarrà nella posizione originale. Se si sceglie di copiare il file nel progetto, Visual Studio crea una copia, lo aggiunge al progetto e viene modificata la connessione in modo che punti alla copia. Vengono modificate anche le altre connessioni, ad esempio quelli in Esplora Server.  
  
 L'impostazione predefinita della proprietà dipende dal tipo di file di database in che uso. Il comportamento dei **Copy to Output Directory** proprietà non è applicabile ai progetti Web o C++.  
  
 Durante lo sviluppo, si potrebbe voler visualizzare gli effetti del codice per il database senza apportare tali modifiche permanenti. È possibile farlo dall'impostazione delle **Copy to Output Directory** proprietà del file su true. Ogni volta che il progetto viene compilato o si preme F5, il file viene copiato nella cartella bin e vengono apportate modifiche a tale file, non per il file nella cartella radice del progetto. Il file di database nella cartella radice del progetto viene modificato solo quando si modifica lo schema di database o i dati mediante **Esplora Server**, **Esplora Database** o altre finestre degli strumenti.  
  
 Nella tabella seguente descrive le impostazioni del **Copy to Output Directory** proprietà.  
  
|Impostazione|Comportamento|  
|-------------|--------------|  
|**Copia se più recente** (impostazione predefinita per i file sdf)|Il file di database viene copiato dalla directory del progetto per la **bin** tempo alla prima il progetto viene compilato. Ogni successiva compilazione del progetto, il **Data ultima modifica** viene confrontato con proprietà dei file. Se il file nella cartella del progetto è più recente, viene copiato per la **bin** cartella, sostituendo il file che è attualmente disponibile. Se il file nei **bin** cartella è più recente, viene copiato alcun file. Questa impostazione vengono mantenute tutte le modifiche apportate ai dati durante la fase di esecuzione, vale a dire che ogni volta che si esegue l'applicazione e salvare le modifiche ai dati, tali modifiche siano visibili alla successiva che esecuzione dell'applicazione. **Attenzione:** questa opzione per i file con estensione mdb o mdf non è consigliata. Il file di database può essere modificato anche quando non vengono apportate modifiche ai dati. È sufficiente aprire una connessione su un file di dati (ad esempio, espandendo il **tabelle** nodo **Esplora Server**) possibile contrassegnarlo come più recente.|  
|**Copia sempre** (impostazione predefinita per i file con estensione mdf e mdb)|Il file di database viene copiato dalla directory del progetto nella directory /bin ogni volta che si compila l'applicazione. Pertanto, se si compila la tua applicazione e salvare le modifiche apportate al file nella directory /bin, tali modifiche vengono sovrascritte la volta successiva che il file originale viene copiato nella directory /bin.|  
|**Non copiare**|Il file non viene mai copiato o sovrascritto dal sistema del progetto. È necessario copiare manualmente il file dalla directory del progetto nella directory di output se si usa questa impostazione.|  
  
## <a name="procedure"></a>Routine  
  
#### <a name="to-respond-to-the-local-database-file-dialog-box"></a>Per rispondere a nella finestra di dialogo del file di database locale  
  
-   Fare clic su **Sì** se si vuole che Visual Studio per copiare il file di database nel progetto e modificare la connessione in modo che punti alla copia nel progetto. Per altre informazioni sull'utilizzo dei file di database nel progetto, vedere [Cenni preliminari sui dati locali](../data-tools/local-data-overview.md).  
  
-   Fare clic su **No** se non si desidera copiare il file di database nel progetto Visual Studio. Al contrario, i punti di connessione per il file nel percorso originale e il file di database non viene aggiunto come un file al progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Connessione ai dati in un File di Database locale (Windows Form)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Connettersi ai dati in un database di Access (Windows Form)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)