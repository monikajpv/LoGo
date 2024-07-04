![image](https://github.com/monikajpv/LoGo/assets/100360728/39bd3c3d-63c0-4d0a-a161-98ab0cee046a)

Explanation:
To create these logo I have used SVG which is (Scalable Vector Graphics) it is a powerful XML-based markup language used to describe two-dimensional vector graphics. 
It's widely used in web development for creating interactive and responsive graphical elements.

<svg> Begins the SVG element.
width="400" height="400": Sets the width and height of the SVG canvas to 400x400 pixels.
viewBox="0 0 200 200": Defines the coordinate system and aspect ratio .

<g transform="rotate(45 100 100)">: Groups the SVG elements and applies a rotation to it.

These <rect> elements represent colored rectangles inside the rotated group 
x, y, width, height, and fill attributes specify position, dimensions, and color of the diamond shape.

Assignment No: 2
Algorithm and Data Structure


1. Declare and Initialize the data:
    Started from Kiev.
    Create an empty list "route" to store the cities in the order they are visited.

2. As the son started with Kiev Add "Kiev" to the "route".

3. Finding the next city:
    Look for a ticket that starts from the last city added to "route".

4. Update the route:
    Add the destination city from the ticket to "route".
    Mark the ticket as used or remove it from the available tickets.

5. Repeat the steps 3 & 4 until all cities have been visited exactly once.

6. Print "route" list which represents the route your son traveled.
 Route traveled by son: ['Kiev', 'Prague', 'Zurich', 'Amsterdam', 'Barcelona', 'Berlin', 'Kiev']



def find_route(start_city, tickets):

    graph = defaultdict(list)
    for ticket in tickets:
        departure, arrival = ticket.split(' ')
        graph[departure].append(arrival)
    
    
    def dfs(city, visited, path):
        path.append(city)
        visited.add(city)
        
        if len(path) == len(tickets) + 1:
            return path
        
        for neighbor in graph[city]:
            if neighbor not in visited:
                result = dfs(neighbor, visited, path)
                if result:
                    return result
        
        path.pop()
        visited.remove(city)
        return none
    
    visited = set()
    path = []
    route = dfs(start_city, visited, path)
    
    if route:
        return route
    else:
        return "No valid route found"


start_city = 'Kiev'
tickets = [
    "Paris-Skopje", "Zurich-Amsterdam", "Prague-Zurich",
    "Barcelona-Berlin", "Kiev-Prague", "Skopje-Paris",
    "Amsterdam-Barcelona", "Berlin-Kiev", "Berlin-Amsterdam"
]

Route traveled by son: ['Kiev', 'Prague', 'Zurich', 'Amsterdam', 'Barcelona', 'Berlin', 'Kiev']


