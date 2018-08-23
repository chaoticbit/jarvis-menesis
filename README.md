# React Modal 

## Installation
`import { Modal } from 'react-modal';`

## Usage ( 2 methods)

* ### Via passing content props
  #### Example
  ```
  const actionButtons = [
    { name: "Done", theme: "base" },
    { name: "Cancel", theme: "default" }
  ];
  
  class App extends Component {
    state = {
      modalOpen: false,
    }

    renderModal = () => {
      if (this.state.modalOpen) {
        return (
          <Modal
            isOpen={this.state.modalOpen}
            onExit={this.onExit.bind(this)}
            onOpen={this.onOpen.bind(this)}
            onClose={this.onClose.bind(this)}
            title="Welcome to Soapbox"
            buttons={actionButtons}
            keystrokes={false}
            textAligned="center"
            content="This is modal content"
            size="small"
            type="dialog"
          />
        );
      }
    }

    render() {
      return (
        <div className="App">
          {this.renderModal()}
          <button
            className="btn btn-primary"
            onClick={() => this.setState({ modalOpen: true })}>
            Toggle Modal
          </button>
        </div>
      );
    }
  }
  ```

* ### Defining custom modal content
  #### Example
  ```
  class App extends Component {
    state = {
      modalOpen: false,
    }

    renderModal = () => {
      if (this.state.modalOpen) {
        return (
          <Modal
            isOpen={this.state.modalOpen}
            onExit={this.onExit.bind(this)}
            onOpen={this.onOpen.bind(this)}
            onClose={this.onClose.bind(this)}
            keystrokes={false}
            textAligned="center"
            size="small">
              <div className="rct-modal-header">
                <p className="title">Modal Title</p>
              </div>
              <div className="rct-modal-body">
                Here goes the modal content
              </div>
              <div className="rct-modal-footer">
                <div className="filler">
                  <button
                    className={`action-button base`}
                    onClick={() => this.onExit("done")}>
                    Done
                  </button>
                  <button
                    className={`action-button default`}
                    onClick={() => this.onExit("cancel")}>
                    Cancel
                  </button>
               </div>
             </div>
           </Modal>
          );
       }
    }

    render() {
      return (
        <div className="App">
          {this.renderModal()}
          <button
            className="btn btn-primary"
            onClick={() => this.setState({ modalOpen: true })}>
            Toggle Modal
          </button>
        </div>
      );
    }
  }
  ```
  
### `onExit(type)` prop callback usage
  
   **type** is 
   1. the name in lowercase you pass to actionButtons array<br/>
    `eg: const actionButtons = [{ name: "Remove", theme: "error"}]`
  
   2. manually pass in the button tag<br/>
     ```
     <button
        className={`action-button error`}
        onClick={() => this.onExit("delete")}>Delete</button>
     ```

  ```  
  onExit(type) {
      type is 'remove' in first example
      type is 'delete' in second example

      //perform some logic and close the modal
      switch (type) {
          case "remove/delete":
              this.setState({ modalOpen: false });
              break;
          default:
              this.setState({ modalOpen: false });
      }
  }
  ```
