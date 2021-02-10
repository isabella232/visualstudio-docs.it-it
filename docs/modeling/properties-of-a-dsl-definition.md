---
title: Proprietà di una definizione DSL
description: Informazioni sulle proprietà di DslDefinition che definiscono le proprietà di definizione del linguaggio specifiche del dominio, ad esempio la numerazione delle versioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ef8f49e46c554efca89862c787fbfbe97c48c8f4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959116"
---
# <a name="properties-of-a-dsl-definition"></a>Proprietà di una definizione DSL
Le proprietà di DslDefinition definiscono le proprietà della definizione del *linguaggio specifico di dominio* , ad esempio la numerazione delle versioni. Le proprietà di DslDefinition vengono visualizzate nella finestra **Proprietà** quando si fa clic su un'area aperta del diagramma nel *finestra di progettazione Domain-Specific Language*.

 Per ulteriori informazioni, vedere [come definire un linguaggio Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzazione ed estensione di un linguaggio Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition presenta le proprietà riportate nella tabella seguente:

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Modificatore di accesso|Determina se il modificatore di accesso per la classe di dominio è pubblico o interno.|public|
|Attributi personalizzati|Attributi definiti personalizzati per la classe di dominio.<br /><br /> **Nota** Usare il pulsante Sfoglia per aggiungere un attributo.|\<none>|
|Nome società|Nome dell'attuale nome della società nel registro di sistema.|Nome società corrente|
|Nome|Nome di questa classe di dominio.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi affiliato a questa classe di dominio.|Spazio dei nomi corrente|
|GUID pacchetto|GUID del pacchetto Visual Studio generato per questo linguaggio DSL.|\<none>|
|Spazio dei nomi del pacchetto|Spazio dei nomi per il pacchetto Visual Studio generato per questo linguaggio DSL.|\<none>|
|Nome prodotto|Nome del prodotto che verrà registrato per il pacchetto Visual Studio generato per il linguaggio DSL.|\<none>|
|Note|Note associate a questa classe di dominio.|\<none>|
|Descrizione|Descrizione per questa classe di dominio.|\<none>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questa classe di dominio.|\<none>|
|Parola chiave della Guida|Parola chiave della Guida associata a questa classe di dominio.|\<none>|
|Compilazione|Numero di build incrementale per la definizione del linguaggio specifico di dominio.|0|
|Versione principale|Numero di build principale incrementale per la definizione del linguaggio specifico di dominio.|1|
|Versione secondaria|Numero di build secondario incrementale per la definizione del linguaggio specifico di dominio.|0|
|Revisione|Numero di build di revisione incrementale per la definizione del linguaggio specifico di dominio.|0|

## <a name="see-also"></a>Vedere anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))