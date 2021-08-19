---
title: '&lt;Elemento &gt; PackageFiles (programma di avvio automatico) | Microsoft Docs'
description: Informazioni sull'elemento PackageFiles, che contiene gli elementi PackageFile che definiscono i pacchetti di installazione eseguiti come risultato dell'elemento Command.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <PackageFiles> element [bootstrapper]
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: d986c13a4c575fa70dd4496c0b87073baa1615f7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080377"
---
# <a name="ltpackagefilesgt-element-bootstrapper"></a>&lt;Elemento PackageFiles &gt; (programma di avvio automatico)
`PackageFiles`L'elemento contiene elementi che definiscono i pacchetti di installazione `PackageFile` eseguiti come risultato `Command` dell'elemento .

## <a name="syntax"></a>Sintassi

```xml
<PackageFiles
    CopyAllPackageFiles
>
    <PackageFile
        Name
        HomeSite
        CopyOnBuild
        PublicKey
        Hash
    />
</PackageFiles>
```

## <a name="elements-and-attributes"></a>Elementi e attributi
 L'elemento `PackageFiles` presenta l'attributo seguente:

|Attributo|Descrizione|
|---------------|-----------------|
|`CopyAllPackageFiles`|Facoltativa. Se impostato su `false` , il programma di installazione scarica solo i file a cui viene fatto riferimento dall'elemento `Command` . Se impostato su `true` , verranno scaricati tutti i file.<br /><br /> Se impostato su , il programma di installazione si comporterà come se fosse impostato su e in caso contrario si comporterà come `IfNotHomesite` `False` se `ComponentsLocation` `HomeSite` `True` . Questa impostazione può essere utile per consentire ai pacchetti che sono a loro volta programmi di bootstrap di eseguire il proprio comportamento in uno scenario HomeSite.<br /><br /> Il valore predefinito è `true`.|

## <a name="packagefile"></a>PackageFile
 `PackageFile`L'elemento è figlio `PackageFiles` dell'elemento . Un `PackageFiles` elemento deve avere almeno un elemento `PackageFile` .

 `PackageFile` ha gli attributi seguenti.

| Attributo | Descrizione |
|---------------| - |
| `Name` | Obbligatorio. Nome del file del pacchetto. Si tratta del nome a cui `Command` l'elemento farà riferimento quando definisce le condizioni in cui viene installato un pacchetto. Questo valore viene usato anche come chiave nella tabella per recuperare il nome localizzato che verrà usato da strumenti come `Strings` [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per descrivere il pacchetto. |
| `HomeSite` | facoltativo. Percorso del pacchetto nel server remoto, se non è incluso nel programma di installazione. |
| `CopyOnBuild` | facoltativo. Specifica se il programma di avvio automatico deve copiare il file del pacchetto sul disco in fase di compilazione. Il valore predefinito è true. |
| `PublicKey` | Chiave pubblica crittografata del firmatario del certificato del pacchetto. Obbligatorio se `HomeSite` viene utilizzato ; in caso contrario, facoltativo. |
| `Hash` | facoltativo. Hash SHA1 del file del pacchetto. Viene usato per verificare l'integrità del file in fase di installazione. Se non è possibile calcolare l'hash identico dal file del pacchetto, il pacchetto non verrà installato. |

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente vengono definiti i pacchetti per .NET Framework ridistribuibile e le relative dipendenze, ad esempio il programma di Windows.

```xml
<PackageFiles>
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>
    <PackageFile Name="dotnetchk.exe"/>
</PackageFiles>
```

## <a name="see-also"></a>Vedi anche
- [\<Product> Elemento](../deployment/product-element-bootstrapper.md)
- [\<Package> Elemento](../deployment/package-element-bootstrapper.md)
- [Informazioni di riferimento sullo schema di prodotti e pacchetti](../deployment/product-and-package-schema-reference.md)