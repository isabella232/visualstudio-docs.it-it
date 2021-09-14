---
title: Proprietà di una definizione DSL
description: Si apprenderà che le proprietà DslDefinition definiscono proprietà di definizione del linguaggio specifiche del dominio, ad esempio la numerazione delle versioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: cd32788e6b423b5ceb1ceafa54ad72cd3a885b15
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637604"
---
# <a name="properties-of-a-dsl-definition"></a>Proprietà di una definizione DSL
Le proprietà DslDefinition definiscono *proprietà di definizione del linguaggio specifiche* del dominio, ad esempio la numerazione delle versioni. Le proprietà DslDefinition vengono visualizzate nella **finestra Proprietà** quando si fa clic su un'area aperta del diagramma nel *Finestra di progettazione Domain-Specific Language*.

 Per altre informazioni, vedere [How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md). Per altre informazioni su come usare queste proprietà, vedere [Personalizzazione](../modeling/customizing-and-extending-a-domain-specific-language.md)ed estensione di un Domain-Specific language .

 Nella tabella seguente sono disponibili le proprietà di DslDefinition:

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Modificatore di accesso|Determina se il modificatore di accesso per la classe di dominio è pubblico o interno.|public|
|Attributi personalizzati|Attributi definiti personalizzati per la classe di dominio.<br /><br /> **Nota** Usare il pulsante Sfoglia per aggiungere un attributo.|\<none>|
|Nome società|Nome della società corrente nel Registro di sistema.|Nome società corrente|
|Nome|Nome di questa classe di dominio.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi affiliato a questa classe di dominio.|Spazio dei nomi corrente|
|GUID del pacchetto|GUID del pacchetto Visual Studio generato per questo linguaggio DSL.|\<none>|
|Spazio dei nomi del pacchetto|Spazio dei nomi per il pacchetto Visual Studio generato per questo linguaggio DSL.|\<none>|
|Nome prodotto|Nome del prodotto che verrà registrato per il pacchetto Visual Studio generato per il linguaggio DSL.|\<none>|
|Note|Note associate a questa classe di dominio.|\<none>|
|Descrizione|Descrizione per questa classe di dominio.|\<none>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questa classe di dominio.|\<none>|
|Parola chiave della Guida|Parola chiave della Guida associata a questa classe di dominio.|\<none>|
|Compilazione|Numero di build incrementale per questa definizione del linguaggio specifica del dominio.|0|
|Versione principale|Numero di build principale incrementale per questa definizione del linguaggio specifico di dominio.|1|
|Versione secondaria|Numero di build secondario incrementale per questa definizione del linguaggio specifico di dominio.|0|
|Revisione|Numero di build della revisione incrementale per questa definizione del linguaggio specifico di dominio.|0|

## <a name="see-also"></a>Vedere anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))