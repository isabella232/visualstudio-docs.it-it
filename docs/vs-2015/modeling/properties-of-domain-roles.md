---
title: Proprietà dei ruoli di dominio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a0cddfb3d5c95e5636e9dac069106e3010bedff8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671459"
---
# <a name="properties-of-domain-roles"></a>Proprietà dei ruoli di dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le proprietà nella tabella seguente sono associate a un ruolo di dominio. Per informazioni sui ruoli di dominio, vedere informazioni su [modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzazione ed estensione di un Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Proprietà|Descrizione|Predefinito|
|--------------|-----------------|-------------|
|Tipo di raccolta|Se questo ruolo ha molteplicità pari a 0.. * o 1.. \* , questa proprietà Personalizza il tipo generico usato per archiviare la raccolta di collegamenti.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> viene utilizzato|
|Attributi personalizzati|Gli attributi specificati qui verranno aggiunti come attributi alla classe di codice generata.|\<none>|
|Proprietà esplorabile|Se `True` , e se la molteplicità della relazione è 0.. 1 o 1.. 1, la proprietà Role può essere esplorata dall'utente nella finestra **Proprietà** . La proprietà Visualizza il nome dell'elemento all'altra estremità del collegamento della relazione.|`True`|
|Generatore di proprietà|Se `True` , viene generata una proprietà Role per questo ruolo, che è possibile utilizzare per attraversare la relazione nel codice del programma. Se si imposta questo valore su false, è possibile attraversare la relazione in modo meno efficiente utilizzando metodi statici della relazione di dominio.|`True`|
|Modificatore di accesso getter proprietà|Modificatore di accesso per il getter per la proprietà generata ( `public` , `internal` , `private` , `protected` o `protected internal` ).|`public`|
|Modificatore di accesso Setter proprietà|Modificatore di accesso per il setter per la proprietà generata ( `public` ,, `internal` `private` , `protected` o `protected internal` ).|`public`|
|Molteplicità|Numero di elementi del modello in cui è possibile riprodurre il ruolo opposto ( `0..1` ,, `1..1` `0..*` o `1..*` ). Se la molteplicità è `0..*` o `1..*` , la proprietà generata rappresenta una raccolta. in caso contrario, la proprietà generata rappresenta un singolo elemento del modello.|Dipende dal tipo di relazione e dal fatto che questo sia il ruolo di origine o di destinazione nella relazione.|
|Nome|Nome del ruolo del dominio. Questa proprietà non può contenere spazi vuoti.|Nome della classe di dominio dell'assegnatario di ruolo per questo ruolo.|
|Propaga la copia|`DoNotPropagateCopy` -L'assegnatario di ruolo copiato non avrà alcuna copia di questo collegamento.<br /><br /> `PropagateCopyToLinkOnly` -Il collegamento copiato punta all'assegnatario di ruolo opposto esistente.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` -Il collegamento copiato punta a una copia dell'assegnatario di ruolo opposto.|`PropagateCopyToLinkAndOppositeRolePlayer` per i ruoli di origine degli incorporamenti.<br /><br /> `DoNotPropagateCopy` per altri ruoli.<br /><br /> Per altre informazioni, vedere [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md)|
|Propaga l'eliminazione|`True` per eliminare l'elemento che svolge questo ruolo quando il collegamento associato viene eliminato.|`True` per la destinazione di un ruolo di incorporamento.<br /><br /> `False` per altri ruoli.<br /><br /> Per altre informazioni, vedere [personalizzazione del comportamento di eliminazione](../modeling/customizing-deletion-behavior.md).|
|Nome proprietà|Nome della proprietà generata nel codice dell'assegnatario di ruolo. Questo nome non può contenere spazi vuoti.|Nome del ruolo opposto se il ruolo ha una molteplicità zero-a-uno o uno-a-uno. in caso contrario, il nome plurale del ruolo opposto.|
|Assegnatario di ruolo|Classe di dominio dell'elemento che può riprodurre questo ruolo nella relazione. Questa proprietà è di sola lettura.|Classe di dominio dell'assegnatario di ruolo per questo ruolo.|
|Note|Note informali associate al ruolo del dominio.|\<none>|
|Category|Categoria in cui la proprietà generata viene visualizzata nella finestra **Proprietà** della finestra di progettazione generata. Se questa proprietà è vuota, la proprietà generata viene visualizzata sotto la categoria **varie**|\<none>|
|Descrizione|Descrizione utilizzata per documentare il codice e utilizzata nell'interfaccia utente della finestra di progettazione generata.<br /><br /> La descrizione viene visualizzata nella descrizione comando IntelliSense per la proprietà generata nella classe assegnatario di ruolo.|`Description for`*nome completo del ruolo*|
|Nome visualizzato|Nome visualizzato nella finestra di progettazione generata per il ruolo di dominio.|Valore regolato della proprietà Name.|
|Parola chiave della Guida|Parola chiave facoltativa utilizzata per indicizzare la Guida sensibile al contesto per il ruolo di dominio.|\<none>|
|Nome visualizzato proprietà|Nome visualizzato nella finestra di progettazione generata per la proprietà del ruolo generata.|Valore regolato della proprietà del nome della proprietà.|

> [!NOTE]
> Il valore predefinito di un nome visualizzato è basato sul valore della proprietà associata inserendo spazi prima di ogni carattere maiuscolo preceduto da un carattere minuscolo e non seguito da un altro carattere maiuscolo.

## <a name="see-also"></a>Vedere anche
 [Proprietà delle relazioni di dominio](../modeling/properties-of-domain-relationships.md)
