---
title: Proprietà di una definizione DSL
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c7ff2be87a91e6c01ec275bcff1d77aa6481df1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658286"
---
# <a name="properties-of-a-dsl-definition"></a>Proprietà di una definizione DSL
Le proprietà di DslDefinition definiscono le proprietà della definizione del *linguaggio specifico di dominio* , ad esempio la numerazione delle versioni. Le proprietà di DslDefinition vengono visualizzate nella finestra **Proprietà** quando si fa clic su un'area aperta del diagramma nel *finestra di progettazione Domain-Specific Language*.

 Per ulteriori informazioni, vedere [come definire un Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzazione ed estensione di un Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition presenta le proprietà riportate nella tabella seguente:

|proprietà|Descrizione|Impostazione predefinita|
|-|-|-|
|Modificatore di accesso|Determina se il modificatore di accesso per la classe di dominio è pubblico o interno.|public|
|Attributi personalizzati|Attributi definiti personalizzati per la classe di dominio.<br /><br /> **Nota** Usare il pulsante Sfoglia per aggiungere un attributo.|\<nessuno>|
|Nome società|Nome dell'attuale nome della società nel registro di sistema.|Nome società corrente|
|Name|Nome di questa classe di dominio.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi affiliato a questa classe di dominio.|Spazio dei nomi corrente|
|GUID pacchetto|GUID per il pacchetto di Visual Studio generato per questo DSL.|\<nessuno>|
|Spazio dei nomi del pacchetto|Spazio dei nomi per il pacchetto di Visual Studio generato per questo DSL.|\<nessuno>|
|Nome prodotto|Nome del prodotto che verrà registrato per il pacchetto di Visual Studio generato per questo DSL.|\<nessuno>|
|Note|Note associate a questa classe di dominio.|\<nessuno>|
|Descrizione|Descrizione per questa classe di dominio.|\<nessuno>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questa classe di dominio.|\<nessuno>|
|Parola chiave della Guida|Parola chiave della Guida associata a questa classe di dominio.|\<nessuno>|
|Compilazione|Numero di build incrementale per la definizione del linguaggio specifico di dominio.|0|
|Versione principale|Numero di build principale incrementale per la definizione del linguaggio specifico di dominio.|1|
|Versione secondaria|Numero di build secondario incrementale per la definizione del linguaggio specifico di dominio.|0|
|Revision|Numero di build di revisione incrementale per la definizione del linguaggio specifico di dominio.|0|

## <a name="see-also"></a>Vedere anche

- [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)