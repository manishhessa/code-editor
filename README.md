# code-editor
this is code editor in react
codeeditor.js :
import React,{useState} from "react";
// import { ReactTransliterate } from "./Translator/index";
// import Highlight, { defaultProps } from "prism-react-renderer";
// import Dark from "prism-react-renderer/themes/nightOwl";
// import Light from "prism-react-renderer/themes/duotoneLight";

import {
  File,
  FileCheck,
  // BrightnessHigh,
  // MoonFill,
} from "react-bootstrap-icons";
import "./CodeEditor.css";
// import { languages } from './languages';

const CodeEditor = ({
  texteditor,
  handleChange,
  // handleKeyDown,
  // handleCode,
  input,
  handleInput,
  customInput,
  setcustomInput,
}) => {
  const [lines, setLines] = useState(1);
  const handleLineChange = (event) => {
    const lines = event.target.value.split("\n").length;
    setLines(lines);
    handleChange(event);
  };

  const lineNumbers = [];
  for (let i = 1; i <= lines; i++) {
    lineNumbers.push(<div key={i}>{i}</div>);
  }
 
  //manish hessa
  // function MyComponent() {
  //   const numTabs = 3;
  //   const tabs = "\t".repeat(numTabs);
  //   return (
  //     <div>
  //       <p>{tabs}</p>
  //     </div>
  //   );
  // }

  // const [lang, setLang] = useState("hi");
  // const [dark, setDark] = useState(true);
  // const [disable, setDisable] = useState(true);

  // const theme = dark ? Dark : Light

  // const styles = {
  //   root: {
  //     boxSizing: 'border-box',
  //     fontFamily: '"Dank Mono", "Fira Code", monospace',
  //     minHeight: '200px',
  //     backgroundColor:'#000000',
  //     ...theme.plain
  //   }
  // }

  // const [show, setShow] = useState(false)

  // const componentRef = useRef();

  // const highlight = code => (
  //   <Highlight {...defaultProps} theme={dark? Dark : Light} code={code} language="py">
  //     {({ className, style, tokens, getLineProps, getTokenProps }) => (
  //       <Fragment>
  //         {tokens.map((line, i) => (
  //           <div {...getLineProps({ line, key: i })}>
  //             {line.map((token, key) => <span {...getTokenProps({ token, key })} />)}
  //           </div>
  //         ))}
  //       </Fragment>
  //     )}
  //   </Highlight>
  // )

  return (
    <div className="code-editor-container">
      {/* {<MyComponent />} */}
      <div className="line-numbers">{lineNumbers}</div>
      <textarea
        value={texteditor}
        onChange={handleLineChange}
        className="editor_class mt-1 multi-input p-1"
      ></textarea>


      {/* <div>
        <span>First item</span>
        {"\t"}
        <span>Second item</span>
      </div> */}

      {/* <ReactTransliterate
        language="python"
        Component="textarea"
        highlight={highlight}
        translate={disable}
        value={texteditor}
        onChange={handleChange}
        onKeyDown={handleKeyDown}
        padding={14}
        style={styles.root}
        lang={lang}
        className="rounded mb-3"
      /> */}

      <div className="d-flex justify-content-start">
        <div>यूजर इनपुट </div>
        <div onClick={setcustomInput}>
          {customInput ? (
            <FileCheck color="green" size={20}/>
          ) : (
            <File size={20} />
          )}
        </div>
      </div>
      {customInput ? (
        <textarea
          className="custom_input mt-1 multi-input p-1"
          value={input}
          onChange={handleInput}
        />
      ) : null}
    </div>
  );
};

export default CodeEditor;





##CodeEdditor.css 

textarea.editor_class {
  width: 100%;
  height: 300px;
  background-color: #081424;
  color: #eee;
  border-radius: 0.3rem;
  padding: 0.5rem;
}

textarea.custom_input {
  width: 100%;
}
.line-number{
  display: inline;
}
.output_box {
  width: 100%;
  padding: 0.5rem;
  background-color: rgb(235, 235, 235);
  border-radius: 0.3rem;
  height: 300px;
  overflow-y: auto;
  border: 5px solid rgba(232, 232, 232, 0.845);
}
.output_textarea {
  width: 100%;
  height: 300px;
  padding: 0.5rem;
  background-color: rgb(235, 235, 235);
  border-radius: 0.3rem;
  outline: none;
  border: 1px solid rgb(192, 192, 192);
}
@media screen and(max-width:600px) {
  textarea.editor_class {
    padding: 0.1rem;
  }
}
