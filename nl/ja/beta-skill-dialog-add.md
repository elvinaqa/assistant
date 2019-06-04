---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-21"

subcollection: assistant

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:deprecated: .deprecated}
{:important: .important}
{:note: .note}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# ダイアログ・スキルの作成
{: #beta-skill-dialog-add}

{{site.data.keyword.conversationshort}} サービスの自然言語処理は、*ダイアログ・スキル* 内で定義されます。ダイアログ・スキルは、会話フローを定義するすべての成果物のコンテナーです。
{: shortdesc}

この機能は、ベータ・プログラムの参加者のみ使用できます。アクセス権を要求する方法については、[ベータ・プログラムへの参加](/docs/services/assistant?topic=assistant-feedback#feedback-beta)を参照してください。

![ベータ](images/beta.png) IBM は、ベータに分類される評価のためのサービス、機能、および言語サポートをリリースしています。 これらの機能は不安定な場合があり、頻繁に変更される場合があり、十分な通知期間を設けずに中止される場合があります。 また、ベータ機能では、通常使用できる機能と同レベルのパフォーマンスや互換性が提供されない場合があり、実稼働環境での使用が意図されていません。 

アシスタントには 1 つのダイアログ・スキルを追加できます。プランごとの制限について詳しくは、[スキルの制限](/docs/services/assistant?topic=assistant-skill-add#skill-add-limits)を参照してください。

## ダイアログ・スキルの作成
{: #beta-skill-dialog-add-task}

スキルを最初から作成することも、IBM によって提供されているサンプル・スキルを使用することも、JSON ファイルからスキルをインポートすることもできます。

[概説チュートリアル](/docs/services/assistant?topic=assistant-getting-started#getting-started-prerequisites)の前提条件ステップを実行し、{{site.data.keyword.conversationshort}} サービス・インスタンスを作成して、ツールを起動してください (まだ実行していない場合)。

{{site.data.keyword.conversationshort}} ツールを使用してスキルを作成します。ダイアログ・スキルを作成するには、次の手順に従ってください。

1.  **「スキル (Skills)」**タブをクリックします。

    一般出荷可能バージョンの {{site.data.keyword.conversationshort}} サービス (旧称 Watson Conversation) で作成されたワークスペースを作成したか、そのワークスペースへの開発者役割のアクセス権を付与されている場合、それらのワークスペースがダイアログ・スキルとしてここにリスト表示されます。
    {: note}

1.  **「新規作成 (Create new)」**をクリックします。

1.  **「追加 (Add)」**をクリックして、*ダイアログ・スキル* を作成します。

1.  以下のいずれかを実行します。

    - スキルを最初から作成するには、**「スキルの作成 (Create skill)」**をクリックします。
    - 本サービスに付属のサンプル・スキルを追加するには、**「サンプル・スキルの使用 (Use sample skill)」**をクリックしてから、使用するサンプルをクリックします。このサンプルを自分で作成するスキルの開始点として使用することもできますし、自分で作成する前にスキルについて調べるための例として使用することもできます。

      サンプル・スキルがスキルのリストに追加されます。これは、アシスタントには関連付けられていません。この手順の残りのステップはスキップしてください。

    - 既存のスキルをこのサービス・インスタンスに追加するには、そのスキルを JSON ファイルとしてインポートします。**「スキルのインポート (Import skill)」**をクリックしてから**「JSON ファイルの選択 (Choose JSON File)」**をクリックし、インポートする JSON ファイルを選択します。

      **重要:**

      - インポートする JSON ファイルは UTF-8 エンコード方式を使用している必要があります。
      - スキルの JSON ファイルの最大サイズは 10MB です。 これよりも大きなスキルをインポートする必要がある場合は、スキルをインポートした後にインテントとエンティティーを別々にインポートする方法を検討してください。 (サイズの大きなスキルは、REST API を使用してインポートすることもできます。 詳しくは、『[API リファレンス ![「外部リンク」アイコン](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/conversation/api/v1/#create_workspace){: new_window}』を参照してください。)
      - JSON にはタブ、改行、復帰を含めることができません。

      含めるデータを指定します。

        - ダイアログも含め、エクスポートされたスキルの完全なコピーをインポートする場合は、**「すべて (インテント、エンティティー、およびダイアログ) (Everything (Intents, Entities, and Dialog))」**を選択します。
        - エクスポートしたスキルのインテントとエンティティーは使用するが、ダイアログは新しいものを作成する予定の場合は、**「インテントとエンティティー (Intents and Entities)」**を選択します。

      **「インポート」**をクリックします。

      スキルのインポート時に問題が発生した場合は、[スキルのインポートに関する問題のトラブルシューティング](#beta-skill-dialog-add-import-errors)を参照してください。

1.  スキルの詳細を指定します。

    - **名前 (Name)**: 長さ 100 文字以下の名前です。 名前は必須です。
    - **説明 (Description)**: 長さ 200 文字以下のオプションの説明です。
    - **言語 (Language)**: トレーニングの対象となるスキルのユーザー入力の言語です。 デフォルト値は英語です。

スキルは、作成された後、「スキル (Skills)」ページにタイルとして表示されます。これで、ダイアログ・スキルで取り扱うユーザー目標の指定を始めることができます。

- 事前に作成されたインテントをスキルに追加するには、[コンテンツ・カタログの使用](/docs/services/assistant?topic=assistant-catalog)を参照してください。
- 独自のインテントを定義するには、[インテント](/docs/services/assistant?topic=assistant-intents)を参照してください。

ダイアログ・スキルは、アシスタントに追加されてそのアシスタントがデプロイされるまでは、お客様と対話できません。詳しくは、[アシスタントの作成](/docs/services/assistant?topic=assistant-assistant-add)を参照してください。

### スキルのインポートに関する問題のトラブルシューティング
{: #beta-skill-dialog-add-import-errors}

サービス・プランによって課された制限を超える成果物がスキルに含まれているという内容のメッセージを受け取った場合は、以下のステップを実行するとスキルのインポートを正常に行うことができます。

1.  成果物の制限値がより高いプランを購入します。
1.  新規プランでサービス・インスタンスを作成します。
1.  新規サービス・インスタンスにスキルをインポートします。
1.  今後使用するプランの成果物の制限要件を満たすようにスキルを編集します。例えば、ダイアログ・ツリーで使用されるダイアログ・ノードの数を減らすことが必要になる場合があります。
1.  編集したスキルをダウンロードしてエクスポートします。
1.  編集したスキルを、必要なプランの元のサービス・インスタンスにもう一度インポートしてみます。

### アシスタントへのスキルの追加
{: #beta-skill-dialog-add-to-assistant}

1 つのアシスタントに 1 つのスキルを追加できます。アシスタント・タイルを開いて、アシスタント構成ページからアシスタントにスキルを追加する必要があります。スキル構成ページ内からは、スキルを使用するアシスタントを選択できません。1 つのダイアログ・スキルを複数のアシスタントで使用することができます。

1.  「アシスタント (Assistants)」タブから、スキルを追加するアシスタントのタイルをクリックして開きます。

1.  **「ダイアログ・スキルの追加 (Add Dialog Skill)」**をクリックします。

1.  **「既存のスキルの追加 (Add existing skill)」**をクリックします。

    表示されている使用可能なスキルから、追加するスキルをクリックします。

    一般出荷可能バージョンの {{site.data.keyword.conversationshort}} サービス (旧称 Watson Conversation) で作成されたワークスペースを作成したか、そのワークスペースへの開発者役割のアクセス権を付与されている場合、既存のダイアログ・スキルを追加するときに、それらのワークスペースがダイアログ・スキルとしてここにリスト表示されます。
    {: note}

## ダイアログ・スキルのダウンロード
{: #beta-skill-dialog-add-download}

JSON 形式でダイアログ・スキルをダウンロードできます。例えば、{{site.data.keyword.conversationshort}} サービスの別のインスタンスで同じダイアログ・スキルを使用する場合に、スキルをダウンロードします。あるインスタンスからスキルをダウンロードして、それを別のインスタンスに新規ダイアログ・スキルとしてインポートできます。

ダイアログ・スキルをダウンロードするには、以下の手順を実行します。

1.  「スキル」ページで、またはスキルを使用するアシスタントの構成ページで、そのダイアログ・スキルのタイルを見つけます。

1.  ![オプション・リストのオープンとクローズ](images/kabob-beta.png) アイコンをクリックしてから、**「JSON のダウンロード (Download JSON)」**を選択します。

1.  JSON ファイルの名前と保存場所を指定して、**「保存 (Save)」**をクリックします。

API を使用してスキルをエクスポートすることもできます。要求に `export=true` パラメーターを組み込みます。詳しくは、[API リファレンス](https://cloud.ibm.com/apidocs/assistant#get-information-about-a-workspace)を参照してください。

## チーム・メンバーとのダイアログ・スキルの共有
{: #beta-skill-dialog-add-invite-others}

サービス・インスタンスを作成した後、そのインスタンスへのアクセス権を他の人々に付与できます。 一緒にトレーニング・データを定義したりダイアログを作成したりすることができます。

それぞれのインテント、エンティティー、ダイアログ・ノードは、一時に 1 人のみが編集できます。 複数の人が同時に同じ項目に対して作業を行うと、最後に変更を保存した人が加えた変更内容だけが適用されます。 同じ時間枠内にその他の人が加えた変更は、先に保存されているので、保持されません。 更新の予定をチーム・メンバーとの間で調整して、全員の作業が失われないようにしてください。
{: important}

ダイアログ・スキルを他のメンバーと共有するには、そのスキルをホストしているサービス・インスタンスに対するアクセス権をメンバーに付与する必要があります。 招待されるメンバーは、このサービス・インスタンスでホストされている任意のスキルにアクセスできるようになることに注意してください。

1.  現行ページの上部に表示されている現在のインスタンス名をメモします。
1.  ページ・ヘッダーの「ユーザー」![ユーザー](images/user-icon2.png) アイコンをクリックして、ドロップダウンから**「ユーザーの管理 (Manage Users)」**を選択します。

1.  **「ユーザーの招待」**をクリックし、アクセス権を付与するチーム・メンバーの E メール・アドレスを入力します。

    Cloud Foundry のサービス・インスタンスへのアクセス権をメンバーに付与した場合、招待されたユーザーとしてそのメンバーが既にリストされていることがあります。そのユーザーの名前をクリックして、アクセス管理設定を開きます。**「アクセス権限の割り当て (Assign access)」**をクリックしてから、**「リソースへのアクセス権限の割り当て (Assign access to resources)」**を選択します。
1.  *「サービス (Services)」*セクションで、少なくとも以下の選択を行います。

    - **サービス**: {{site.data.keyword.conversationshort}}
    - **プラットフォームのアクセス役割の割り当て**: オペレーター

    プラットフォーム管理の役割について詳しくは、[IAM アクセス ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/iam?topic=iam-userroles) を参照してください。(デフォルトでは、サービス・アクセス役割は {{site.data.keyword.conversationshort}} では利用されません。)

    Cloud Foundry で管理される以前のインスタンスについて、*「Cloud Foundry アクセス権限」*セクションを展開し、お客様の組織を選択してから、メンバーを**「開発者」**スペースの役割に割り当てる必要があります。
    {: note}

1.  **「ユーザーの招待」**をクリックします。

    既存のユーザーのアクセス権限を編集している場合は、**「アクセス権限の割り当て (Assign access)」**をクリックします。

招待したメンバーが次回 {{site.data.keyword.cloud_notm}} にログインすると、お客様のアカウントがそれらのメンバーのアカウントのリストに組み込まれます。それらのメンバーがお客様のアカウントを選択すると、メンバーはお客様のサービス・インスタンスを表示し、スキルを開いて編集できるようになります。

ダイアログ・スキルの開発に関与するメンバーが増えるほど、スキルが削除されるなどの、意図しない変更が加えられる可能性が増えます。 必要に応じて旧バージョンにロールバックできるように、ダイアログ・スキルのバックアップ・コピーを定期的に作成することを検討してください。 バックアップは、[スキルを JSON ファイルとしてダウンロード](#beta-skill-dialog-add-download)するだけで作成できます。