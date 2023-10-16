 # Install Package 

 - file 

 bk_itsm_Vx.x.x-ee.tar.gz 

 - file directory structure and function Description 

 Code can be divided into BlueKing App framework layer framework, Flow engine Service layer pipeline, ITSM Business Name layer itsm and front-end display layer web. 

 - framework 

 BlueKing is based on the Two encapsulation architecture of the Django framework, which mainly provided Basic Config and service for SaaS operations on BlueKing PaaS. 

 config: Configuration of each Deploy environment of the project, such as local environment, Test environment, formal environment, and routing configuration. 

 blueapps: Core module of the new App framework, including BlueKing unified signin, authentication, middleware and public Function. 

 - pipeline 

 Self-developed Flow engine framework, mainly including Task process layout page and task process execute Service. 

 conf: Default setting 

 core: Referring to BPMN2.0 specification, core elements such as Activity, Gateway, event and Data are definition 

 models: Storage structure definition and associated methods 

 engine: runtime execute logic and Task Total Manage 

 log: Log persistent Storage and Manage 

 parser: front-end Data Schema parsing 

 validators: Data Check, such as ring structure detection and data validity verification 

 component_framework： Plugin framework and plug-in definition 

 variables: Global Variables definition 

 contrib: extended functionality such Statistics and front-end APIs 

 pipeline_web： Front-end Data adaptation layer, which supports Flow data Generate by front-end canvas 

 pipeline_plugins： Standard OPS Official Plugin library and global customVar 

 - itsm 

 Business Name adaptation layer encapsulated by drf framework, including Flow Manage, Ticket management, Role management, Service management, system setting and other functions. 

 component: Base Module 

 service: Service Manage 

 role: Role Manage 

 workflow: Flow Manage 

 ticket: Ticket Manage 

 wiki: Knowledge Base 

 API: Open API 

 weixin: WeChat Apply 

 - web 

 Front-end Resource, including webpack setting and static resources. 

 frontend: pc and mobile 

 static: static resources root directory 

 templates: page template root directory 

 - locale 

 Internationalization of translated file 

 - docs 

 Interface The document and Other atomHelpDoc 

 - initial 

 system initialization Data 