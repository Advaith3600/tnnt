<script>
    import { AccordionItem, Accordion } from 'flowbite-svelte';
</script>

<div class="container mx-auto py-16 px-6 text-white">
    <div class="grid grid-cols-2 gap-6">
        <div>
            <h2 class="text-3xl font-semibold">What is MEL?</h2>
            <p class="mt-4">
                Implements a set of classes and functions to extract metadata (and textual content) from various file formats, as JSON objects.
            </p>

            <Accordion
                class="mt-8"
                activeClasses="bg-blue-100 dark:bg-slate-600 text-blue-600 dark:text-white"
                inactiveClasses="text-gray-500 dark:text-gray-400 hover:bg-blue-100 dark:hover:bg-gray-600 dark:bg-slate-700"
            >
                <AccordionItem open>
                    <span slot="header">Core Features</span>
                    <ul class="list-disc list-outside pl-4 leading-relaxed text-white/80">
                        <li>Comprehensive metadata extraction support of various file types/formats.</li>
                        <li>File attributes extraction: general metadata.</li>
                        <li>Filetype structure and properties: specific metadata.</li>
                        <li>Structured data associated to the file: associated metadata.</li>
                        <li>Content extraction: raw text and binary-to-text conversion.</li>
                        <li>Analysis of the textual content: pattern matching and keyword extraction.</li>
                        <li>Input: a file; output: a JSON file with the metadata sets and content.</li>
                        <li>It can store the result in a document store (by default, CouchDB).</li>
                        <li>Integrated with The NLP-NER Toolkit for Named Entity Recognition tasks.</li>
                    </ul>
                </AccordionItem>
                <AccordionItem>
                    <span slot="header">Supported File Types/Formats:</span>
                    <ul class="list-disc list-outside pl-4 leading-relaxed text-white/80">
                        <li>.pdf: uses Tesseract-OCR and pdftotext tools.</li>
                        <li>.docx, .pptx: MSO "core properties".</li>
                        <li>.doc, .xls, .ppt, .vsd, .mpp: (generalized to OLE 2 files).</li>
                        <li>.msg: uses Win32 MAPI (Messaging API for Windows) + (OLE 2 file).</li>
                        <li>.docm: uses a C# (.NET) converter.</li>
                        <li>.xlsx</li>
                        <li>.csv</li>
                        <li>.rtf</li>
                        <li>.txt | .xml, .html, .htm, .json: (processed as raw text files)</li>
                        <li>.zip</li>
                        <li>Images: .jpg, .png, etc.</li>
                    </ul>
                </AccordionItem>
            </Accordion>
        </div>

        <div>
            <h2 class="text-3xl font-semibold">What is TNNT?</h2>
            <p class="mt-4">
                Implements a pipeline task to automate the extraction of categorised named entities from the unstructured information encoded in the source documents, using diverse Natural Language Processing (NLP) models and tools. TNNT is integrated with MEL.
            </p>

            <Accordion
                class="mt-8"
                activeClasses="bg-blue-100 dark:bg-slate-600 text-blue-600 dark:text-white"
                inactiveClasses="text-gray-500 dark:text-gray-400 hover:bg-blue-100 dark:hover:bg-gray-600 dark:bg-slate-700"
            >
                <AccordionItem open>
                    <span slot="header">Core Features</span>
                    <ul class="list-disc list-outside pl-4 leading-relaxed text-white/80">
                        <li>Implements 21 models from 9 NLP tools.</li>
                        <li>Capability of processing sequentially several blocks of models based on the input settings.</li>
                        <li>Keeps general processing stats of the models processed.</li>
                        <li>Generates an integrated summary of all recognised entities from all the processed models.</li>
                        <li>
                            The results are generated in JSON files (one for each processed model):
                            <ul class="list-disc list-outside pl-8">
                                <li>Each model generates the list of categories of the identified entities.</li>
                                <li>For each recognised entity, the toolkit retrieves its context information: start index in the document text and sentence.</li>
                            </ul>
                        </li>
                        <li>Hybrid processing data flow supported, either from/to the document store (CouchDB) or via direct processing from files.</li>
                        <li>All textual content extracted by MEL (with many supported file types/formats such as PDF, DOCX, MSG, and TXT) is processable for the NLP/NER Toolkit.</li>
                        <li>A built-in RESTful API that provides basic functions to browse the JSON file results and expand/complement/co-relate the NER results by performing other NLP tasks, such as part-of-speech tagging, dependency parsing, co-reference resolution.</li>
                    </ul>
                </AccordionItem>
                <AccordionItem>
                    <span slot="header">Supported NLP-NER tools and models</span>
                    <ul class="list-disc list-outside pl-4 leading-relaxed text-white/80">
                        <li>NLTK.</li>
                        <li>Stanford NER tagger: class_3, class_4, class_7.</li>
                        <li>Stanza.</li>
                        <li>spaCy: en_core_web_sm, en_core_web_md, en_core_web_lg</li>
                        <li>Allen NLP: ELMo_NER, fine-grained_NER.</li>
                        <li>Deep Pavlov: standard_onto, bert_onto, standard_conll2003, bert_conll2003.</li>
                        <li>Polyglot.</li>
                        <li>Flair: standard, ontonotes, fast, fast_ontonotes, pooled.</li>
                        <li>Google BERT.</li>
                    </ul>
                </AccordionItem>
                <AccordionItem>
                    <span slot="header">Recognised Categories</span>
                    <p class="text-white/80">From the implemented models, the toolkit can recognised entities from the following categories:</p>
                    <ul class="list-disc list-outside pl-4 leading-relaxed mt-2 text-white/80">
                        <li>PERSON: People, including fictional.</li>
                        <li>NORP: Nationalities or religious or political groups.</li>
                        <li>FAC: Buildings, airports, highways, bridges, etc.</li>
                        <li>ORG: Companies, agencies, institutions, etc.</li>
                        <li>GPE: Countries, cities, states.</li>
                        <li>LOC: Non-GPE locations, mountain ranges, bodies of water.</li>
                        <li>PRODUCT: Objects, vehicles, foods, etc. (Not services.)</li>
                        <li>EVENT: Named hurricanes, battles, wars, sports events, etc.</li>
                        <li>WORK_OF_ART: Titles of books, songs, etc.</li>
                        <li>LAW: Named documents made into laws.</li>
                        <li>LANGUAGE: Any named language.</li>
                        <li>DATE: Absolute or relative dates or periods.</li>
                        <li>TIME: Times smaller than a day.</li>
                        <li>PERCENT: Percentage, including “%“.</li>
                        <li>MONEY: Monetary values, including unit.</li>
                        <li>QUANTITY: Measurements, as of weight or distance.</li>
                        <li>ORDINAL: "first", "second", etc.</li>
                        <li>CARDINAL: Numerals that do not fall under another type.</li>
                    </ul>
                </AccordionItem>
            </Accordion>
        </div>
    </div>
</div>
