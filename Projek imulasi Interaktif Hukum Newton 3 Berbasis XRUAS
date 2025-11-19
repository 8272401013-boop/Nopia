// Create Scene
const canvas = document.getElementById("renderCanvas");
const engine = new BABYLON.Engine(canvas, true);
const createScene = () => {
  const scene = new BABYLON.Scene(engine);
  const camera = new BABYLON.ArcRotateCamera("camera", Math.PI/2, Math.PI/3, 8, BABYLON.Vector3.Zero(), scene);
  camera.attachControl(canvas, true);

  // Lighting
  const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1,1,0), scene);

  // Objects
  const box = BABYLON.MeshBuilder.CreateBox("box", {size:1}, scene);
  const sphere = BABYLON.MeshBuilder.CreateSphere("sphere", {diameter:1}, scene);
  sphere.position.x = 2;

  // Physics
  scene.enablePhysics();

  const boxImpostor = new BABYLON.PhysicsImpostor(box, BABYLON.PhysicsImpostor.BoxImpostor, {mass:1}, scene);
  const sphereImpostor = new BABYLON.PhysicsImpostor(sphere, BABYLON.PhysicsImpostor.SphereImpostor, {mass:1}, scene);

  // Apply Action Force
  setInterval(() => {
    sphereImpostor.applyForce(new BABYLON.Vector3(-5,0,0), sphere.getAbsolutePosition());
  }, 2000);

  return scene;
}

const scene = createScene();
engine.runRenderLoop(() => scene.render());
