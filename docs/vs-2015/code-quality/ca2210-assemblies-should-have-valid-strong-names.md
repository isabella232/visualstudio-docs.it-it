---
title: 'CA2210: gli assembly devono avere nomi sicuri validi | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8f800a550717abfabdfb9296fc8f6de49d127d73
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548200"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: Gli assembly devono avere nomi sicuri validi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|Category|Microsoft. Design|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un assembly non è firmato con un nome sicuro, non è stato possibile verificare il nome sicuro oppure il nome sicuro non è valido senza le impostazioni correnti del registro di sistema del computer.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola recupera e verifica il nome sicuro di un assembly. Si verifica una violazione se si verifica una delle condizioni seguenti:

- L'assembly non ha un nome sicuro.

- L'assembly è stato modificato dopo la firma.

- L'assembly è con firma ritardata.

- L'assembly è stato firmato in modo errato o la firma non è riuscita.

- L'assembly richiede le impostazioni del registro di sistema per il superamento della verifica. Ad esempio, lo strumento nome sicuro (Sn.exe) è stato usato per ignorare la verifica per l'assembly.

  Il nome sicuro protegge i client dal caricamento involontario di un assembly alterato. Gli assembly con nomi sicuri non devono essere distribuiti al di fuori di scenari molto limitati. Se si condividono o distribuiscono assembly non firmati correttamente, l'assembly può essere alterato, non essere caricato in Common Language Runtime oppure l'utente potrebbe avere la necessità di disabilitare la verifica nel proprio computer. Un assembly privo di nome sicuro ha uno dei seguenti svantaggi:

- Non è possibile verificare le relative origini.

- Il Common Language Runtime non può avvisare gli utenti se il contenuto dell'assembly è stato modificato.

- Non può essere caricato nel Global Assembly Cache.

  Si noti che per caricare e analizzare un assembly con firma ritardata, è necessario disabilitare la verifica per l'assembly.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 **Per creare un file di chiave**

 Usare una delle procedure seguenti:

- Usare lo strumento Assembly Linker (Al.exe) fornito dall' [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK.

- Per la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] versione 1.0 o 1.1, usare l' <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> attributo o.

- Per [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] , usare l'opzione del `/keyfile` `/keycontainer` compilatore o [/keyfile (specificare la chiave o la coppia di chiavi per firmare un assembly)](https://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06) o [/keycontainer (specificare un contenitore di chiavi per firmare un assembly)](https://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e) in C++).

  **Per firmare l'assembly con un nome sicuro in Visual Studio**

1. In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aprire la soluzione.

2. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Proprietà.**

3. Fare clic sulla scheda **firma** , quindi selezionare la casella di controllo **Firma assembly** .

4. In **scegliere un file di chiave con nome sicuro**selezionare **nuovo**.

    Viene visualizzata la finestra **Crea chiave con nome sicuro** .

5. In **nome file di chiave**Digitare un nome per la chiave con nome sicuro.

6. Scegliere se proteggere la chiave con una password, quindi fare clic su **OK**.

7. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul progetto e quindi scegliere **Compila**.

   **Per firmare l'assembly con un nome sicuro all'esterno di Visual Studio**

- Usare lo strumento nome sicuro (Sn.exe) fornito dall' [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK. Per ulteriori informazioni, vedere [Sn.exe (strumento nome sicuro)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola solo se l'assembly viene usato in un ambiente in cui la manomissione del contenuto non costituisce un problema.

## <a name="see-also"></a>Vedere anche
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
 [Procedura: firmare un assembly con un nome sicuro](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [Sn.exe (strumento nome sicuro)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)
