<script>
    import {uk_width} from "..";
    import {getBackgroundColorClass} from "../helpers/background";

    export let title   = "";
    export let meta    = "";
    export let lead    = "";
    export let content = "";

    let _class, classes = [];
    export {_class as class};

    export let width = "";

    export let backgroundColor = "";
    $: {
        classes = [];
        classes.push(getBackgroundColorClass(backgroundColor));
        if(backgroundColor === "primary" || backgroundColor === "secondary"){
            classes.push("uk-light");
        }
        classes = [...classes];
    }

</script>


<article class={"uk-article " + _class + " " + classes.join(" ")} use:uk_width={width}>
    <slot name="header">
        <h2 class="uk-article-title">
            <slot name="title">
                {title}
            </slot>
        </h2>
    </slot>
    <p class="uk-article-meta">
        <slot name="meta">
            {meta}
        </slot>
    </p>
    <p class="uk-text-lead">
        <slot name="lead">
            {lead}
        </slot>
    </p>
    <slot>
        <p>
            {content}
        </p>
    </slot>
</article>