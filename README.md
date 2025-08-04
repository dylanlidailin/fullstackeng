const App = () => {
  const course = 'Half Stack application development'
  const part1 = 'Fundamentals of React'
  const exercises1 = 10
  const part2 = 'Using props to pass data'
  const exercises2 = 7
  const part3 = 'State of a component'
  const exercises3 = 14

  return (
    <div>
      <h1>{course}</h1>
      <p>
        {part1} {exercises1}
      </p>
      <p>
        {part2} {exercises2}
      </p>
      <p>
        {part3} {exercises3}
      </p>
      <p>Number of exercises {exercises1 + exercises2 + exercises3}</p>
    </div>
  )
}

export default App

1.1 Unfortunately, the entire application is in the same component. Refactor the code so that it consists of three new components: Header, Content, and Total. All data still resides in the App component, which passes the necessary data to each component using props. Header takes care of rendering the name of the course, Content renders the parts and their number of exercises and Total renders the total number of exercises.

const App = () => {
  const exercises1 = 10
  const exercises2 = 7
  const exercises3 = 14

  return(
    <div>
      <Header />
      <Content exercises1={exercises1} exercises2={exercises2} exercises3={exercises3} />
      <Total exercises1={exercises1} exercises2={exercises2} exercises3={exercises3} />
    </div>
  )
}

const Header = () => {
  const header = 'Half Stack application development'
  return <h1>{header}</h1>
}

const Content = (props) => {
  return(
    <div>
      <p> Fundamentals of React {props.exercises1}</p>
      <p> Using props to pass data {props.exercises2}</p>
      <p> State of a component {props.exercises3}</p>
    </div>
  )
}

const Total = (props) => {
  return (
    <p>
      Number of exercises {props.exercises1 + props.exercises2 + props.exercises3}
    </p>
  )
}

export default App

1.2 Refactor the Content component so that it does not render any names of parts or their number of exercises by itself. Instead, it only renders three Part components of which each renders the name and number of exercises of one part.


const App = () => {
  console.log('Rendering App')
  const course = 'Half Stack application development'
  const part1 = 'Fundamentals of React'
  const exercises1 = 10
  const part2 = 'Using props to pass data'
  const exercises2 = 7
  const part3 = 'State of a component'
  const exercises3 = 14
  const parts = [
    { part: part1, exercises: exercises1 },
    { part: part2, exercises: exercises2 },
    { part: part3, exercises: exercises3 }
  ]
  return(
    <div>
      <Header course={course} />
      <Content parts={parts} />
      <Total exercises1={exercises1} exercises2={exercises2} exercises3={exercises3} />
    </div>
  )
}

const Header = (props) => {
  return <h1>{props.course}</h1>
}

const Content = (props) => {
  return (
    <div>
      <p>{props.parts[0].part} {props.parts[0].exercises}</p>
      <p>{props.parts[1].part} {props.parts[1].exercises}</p>
      <p>{props.parts[2].part} {props.parts[2].exercises}</p>
    </div>
  )
}

const Total = (props) => {
  return (
    <p>
      Number of exercises {props.exercises1 + props.exercises2 + props.exercises3}
    </p>
  )
}

export default App