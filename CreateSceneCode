import sys
import rospy
from moveit_commander import RobotCommander, PlanningSceneInterface, roscpp_initialize, roscpp_shutdown
from geometry_msgs.msg import PoseStamped

if __name__=='__main__':
    roscpp_initialize(sys.argv)
    rospy.init_node('moveit_py_demo', anonymous=True)
    scene = PlanningSceneInterface()
    robot = RobotCommander()
    rospy.sleep(1)
    # clean the scene
    scene.remove_world_object("block1")
    scene.remove_world_object("block2")
    scene.remove_world_object("block3")
    scene.remove_world_object("block4")
    scene.remove_world_object("table")
    scene.remove_world_object("bowl")
    scene.remove_world_object("box")
    # publish a demo scene
    p = PoseStamped()
    p.header.frame_id = robot.get_planning_frame()
    p.pose.position.x = 0.7
    p.pose.position.y = -0.4
    p.pose.position.z = 0.85
    p.pose.orientation.w = 1.57
    scene.add_box("block1", p, (0.044, 0.044, 0.044))
    p.pose.position.y = -0.2
    p.pose.position.z = 0.175
    p.pose.orientation.w = 50
    scene.add_box("block2", p, (0.044, 0.044, 0.044))
    p.pose.position.x = 0.6
    p.pose.position.y = -0.7
    p.pose.position.z = 0.5
    scene.add_box("block3", p, (0.044, 0.044, 0.044))
    p.pose.position.x = 1
    p.pose.position.y = -0.7
    p.pose.position.z = 0.5
    scene.add_box("block4", p, (0.044, 0.044, 0.044))
    p.pose.position.x = 0
    p.pose.position.y = 0
    p.pose.position.z = 0
    scene.add_mesh("table", p, "table_scaled.stl")
    scene.add_mesh("bowl", p, "bowl_scaled.stl")
    scene.add_mesh("box", p, "box_scaled.stl")
    rospy.sleep(1)
    # pick an object
    robot.right_arm.pick("block2")
    rospy.spin()
    roscpp_shutdown()
